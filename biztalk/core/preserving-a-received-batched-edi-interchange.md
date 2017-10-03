---
title: "En conservant un reçu par lot échange EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10d21b9b-9684-422a-8948-8bd71a4d5a10
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de14760110eedd002ee01527d57f82c3d6a1aa02
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="preserving-a-received-batched-edi-interchange"></a>Conservation d'un échange EDI reçu traité par lot
> [!NOTE]
>  Toutes les options d’interface utilisateur mentionnées dans cette rubrique sont disponibles dans le **paramètres d’hôte Local** page (**paramètres du récepteur** section) des onglets d’accord bidirectionnel de la  **Propriétés de l’accord** boîte de dialogue.  
  
 Lorsque le pipeline de réception EDI conserve un échange EDI entrant par lot, l'analyse normale de chaque document informatisé/message en fichiers XML intermédiaires distincts n'a pas lieu. Le pipeline de réception EDI traite l'échange comme un document unique sans fractionner les documents informatisés/messages. Cela se produit lorsque le **entrants option de traitement par lots** est définie sur **préserver l’échange : suspendre l’échange en cas d’erreur** ou **préserver l’échange : suspendre les documents informatisés sur Erreur**.  
  
 **Validation de schéma**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] valide l'enveloppe d'un lot préservé en utilisant les schémas de lot et les schémas de service. Le schéma de lot est utilisé pour valider le nœud racine du message préservé : les schémas de service sont utilisés pour valider les en-tête et les codes de fin d'échange, de groupe, et de document informatisé. Pour plus d’informations sur les schémas de lot, consultez [schémas de lot EDI](../core/edi-batch-schemas.md). Pour plus d’informations sur les schémas de service, consultez [Service EDI et des schémas de contrôle](../core/edi-service-and-control-schemas.md).  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] valide les documents dans un échange traité par lot à l'aide des schémas de document de votre projet.  
  
 **Traitement côté réception**  
  
 Le Désassembleur EDI traite les lots conservés comme suit :  
  
-   Lorsque le Désassembleur EDI traite un lot pour le conserver, il convertit le format de fichier plat en format XML et ajoute X12InterchangeXML ou EdifactInterchangeXML comme nœud racine XML. Cette opération indique au pipeline d'envoi que l'échange par lot doit être conservé et que le schéma Edifact_BatchSchema ou X12_BatchSchema doit servir à valider le nœud racine.  
  
-   Le Désassembleur ajoute l'attribut DelimiterSetSerializedData au nœud racine d'un message XML par lot afin d'indiquer les séparateurs que le pipeline d'envoi devra utiliser pour générer un échange EDI par lot à partir du message XML. Lorsque le message XML est un lot conservé, l'attribut est défini par le pipeline de réception à partir des séparateurs utilisés dans le message entrant. Lorsque le message XML par lot est produit par l'orchestration du traitement par lot, l'attribut est défini d'après la valeur spécifiée dans les propriétés de l'accord.  
  
-   Le Désassembleur utilise l'un des espaces de noms suivants lorsqu'il crée un échange XML conservé : `http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006/InterchangeXML` ou `http://schemas.microsoft.com/BizTalk/EDI/X12/2006/InterchangeXML`.  
  
-   Le Désassembleur promeut la propriété de contexte `EDI.ReuseEnvelope == True` pour identifier l'échange comme conservé. Ceci vous permet de créer un port d'envoi qui s'abonne à tous les échanges par lot conservés.  
  
    > [!NOTE]
    >  Un document HIPAA n’est pas fractionné en sous-documents si le **entrants option de traitement par lots** a la valeur **préserver l’échange**. Ce sera le cas même si l'annotation subdocument creation break a la valeur « Oui » dans le schéma HIPAA.  
  
 **Erreur lors du traitement**  
  
 Si vous avez sélectionné **préserver l’échange : suspendre l’échange en cas d’erreur** pour le **entrants option de traitement par lots**, tout l’échange sera suspendu en cas d’erreur. Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] suspend l'ensemble de l'échange conservé, la structure de l'échange et le classement des documents informatisés dans l'échange sont conservés. Si une erreur se produit, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] publie une entrée d'erreur consolidée dans le journal des événements. Cette entrée inclut toutes les erreurs au niveau de l'échange, du groupe fonctionnel et des documents informatisés.  
  
 Si vous avez sélectionné **préserver l’échange : suspendre les documents informatisés en cas d’erreur** pour le traitement par lot entrant option, de réception EDI pipeline supprime tout ensemble de transaction non valide à partir de l’échange et procède à la création de l’échange XML. Le fichier XML d'échange ainsi produit est nécessaire pour réutiliser les enveloppes des segments de contrôle (ISA, GS, GE et IEA pour les échanges X12 ou UNA, UNB, UNG, UNE et UNZ pour les échanges EDIFACT). L’échange sera considéré comme un document a été correctement traité. Toutefois, l’erreur sera signalée dans l’Observateur d’événements, et si un accusé de réception fonctionnel est généré, il signale l’erreur. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]créera une entrée distincte dans le journal des événements pour chaque ensemble de la transaction qui comporte des erreurs. Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supprime un document informatisé erroné de l’échange, la structure d’échange et de classement ne soit pas conservé. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]met à jour le nombre de documents informatisés dans l’échange.  
  
 Voici les cas particuliers de suspension des documents informatisés en cas d'erreur :  
  
-   Si tous les documents informatisés d'un groupe sont non valides, chaque document informatisé est suspendu individuellement mais les segments de contrôle du groupe (sans les documents informatisés puisqu'ils ont été abandonnés) sont inclus dans le fichier XML d'échange généré.  
  
-   Si tous les documents informatisés d'un échange sont non valides, chaque document informatisé est suspendu individuellement mais les segments de contrôle de l'échange (sans les documents informatisés puisqu'ils ont été abandonnés) sont inclus dans le fichier XML d'échange généré.  
  
-   Si les segments de contrôle du groupe sont non valides, tous les documents informatisés du groupe sont suspendus individuellement.  
  
-   Si les segments de contrôle de l'échange sont non valides, tous les documents informatisés de l'échange sont suspendus individuellement et le fichier XML de l'échange n'est pas généré. Une entrée est créée dans l'observateur d'événements pour l'échange rejeté.
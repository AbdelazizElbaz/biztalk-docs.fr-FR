---
title: "SWIFT schémas d’en-tête et code de fin | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trailer schemas
- schemas, headers
- schemas, trailers
- header schemas
ms.assetid: 82cd33d4-6bbb-4124-9506-fd35b5dca8a4
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8f3cb45e14a7c7e900fc26a4cbc8fcfb5d7b66e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-header-and-trailer-schemas"></a>SWIFT schémas d’en-tête et code de fin
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fournit le SWIFT schémas d’en-tête et le code de fin. A4SWIFT a déjà incorporé dans les schémas d’échange pour les messages FIN différentes. Si vous souhaitez créer un SWIFT FIN format style message type personnalisé (par exemple, un message N98), vous pouvez incorporer les schémas d’en-tête et le code dans votre propre format.  
  
 Le schéma d’en-tête SWIFT (SWIFT Header.xsd) contient les formats pour les éléments suivants :  
  
-   En-tête de base  
  
-   En-tête de l’application (choix de l’entrée ou sortie)  
  
-   En-tête de l’utilisateur  
  
-   Délimiteur de début du bloc de texte  
  
 L’en-tête de base contient des informations sur la source du message. L’en-tête de l’Application contient des informations sur le type de message et la destination du message. La résolution du type de message par le désassembleur SWIFT dans un pipeline de réception est basée sur le contenu du champ dans l’en-tête d’Application approprié. L’en-tête de l’utilisateur est facultative et contient des instructions de traitement spécial.  
  
> [!NOTE]
>  Certains types de messages ont des formats variables en fonction du contenu du champ 119 dans l’en-tête de l’utilisateur. Il s’agit de « types de message double » dans A4SWIFT. Le désassembleur A4SWIFT utilise le type de message dans l’en-tête de l’Application conjointement avec la valeur du champ 119 pour sélectionner le schéma approprié pour une instance de message.  
  
 Le *SWIFT utilisateur manuel*, qui fait partie de la documentation SWIFT pour le service FIN, décrit toutes ces en-têtes.  
  
 Au début du bloc de texte est « {4 : » suivi d’un retour chariot et un saut de ligne. Au début du bloc de texte est requis.  
  
 Pour prendre en compte (l’analyse et la validation) de traitement des échanges contenant uniquement SWIFT bloc 4, tous les blocs d’en-tête et le code de fin dans les schémas d’échange sont marqués comme facultatifs. Cela s’éloigne de la spécification de la FIN de SWIFT, où le bloc d’en-tête de base 1 et le bloc d’en-tête de l’Application 2 sont obligatoires. Cela vous permet d’utiliser le schéma de l’échange pour traiter les messages qui ne nécessitent pas d’en-têtes. Par exemple, si vous acceptez les messages reçus via FileAct, l’en-tête de lot peut contenir la source des messages ainsi que d’un type de message commun.  
  
 Le fichier DLL du schéma RunTime inclut également le schéma d’en-tête. Installation d’A4SWIFT déploie le fichier DLL du schéma de RunTime et le schéma de propriété A4SWIFT. Si vous avez besoin utiliser votre propre en-tête pour le traitement, vous pouvez définir et déployer un schéma d’en-tête personnalisé et promouvoir les propriétés appropriées pour la résolution de message. Si vous le faites, vous devez également spécifier le nouvel en-tête dans le désassembleur SWIFT (DASM). Le schéma d’en-tête personnalisé n’a pas doit avoir le même Type de Document que le schéma d’en-tête SWIFT que A4SWIFT installation a déployé dans les schémas de RunTime DLL. Veillez à modifier l’espace de noms de schéma, ou le nom du nœud racine ou les deux.  
  
 Le schéma de code de fin SWIFT (**SWIFT Trailer.xsd**) contient le format pour les éléments suivants :  
  
-   Délimiteur de fin du bloc de texte  
  
-   Codes de l’utilisateur (utilisateur et des informations système)  
  
-   Codes de fin système  
  
 Le délimiteur de fin du bloc de texte est «- »}. Le bloc de code de fin commence par « {5 : ». Le contenu du bloc de code de fin inclure des informations sur l’utilisateur (somme de contrôle, l’authentification des messages, d’authentification propriétaire et ainsi de suite) et les informations système (messages retardés, référence du message, possible de messages en double et ainsi de suite). Codes de fin ajoutées par SWIFT fournissent également un bloc de tiers, délimité par « {S: ». Le *SWIFT utilisateur manuel*, sous « Description de Service de FIN », décrit en détail le contenu du bloc 5. A4SWIFT ne valide pas le contenu du bloc S.  
  
 L’interface FIN réelle ou le réseau SWIFT ajoute les codes de fin. Si un message contient un code de fin lorsque A4SWIFT reçoit le message, A4SWIFT exécute le code de fin avec le message. A4SWIFT ne génère pas d’erreur si un message ne contient pas un code de fin lorsque A4SWIFT reçoit le message. Comme avec les en-têtes, toutes les entrées de code de fin, y compris les blocs eux-mêmes, sont facultatives dans A4SWIFT.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de schémas](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)
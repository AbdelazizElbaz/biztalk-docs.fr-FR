---
title: "Schéma Validation2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f9d1576-10df-4c5a-9ae0-618f0dd54b4e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 317fa8e0e5e557993922bba383ebf5eca460fa69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-validation"></a>Validation de schéma
Le pipeline de réception EDI et le pipeline d'envoi EDI valident un message en utilisant les  schémas suivants :  
  
-   **Validation d’enveloppe**: schéma de Service dans `Microsoft.BizTalk.Edi.BaseArtifacts.dll` dans[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]  
  
-   **Validation du document informatisé**: stockent les schémas de Message dans le schéma dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI  
  
-   **Validation de message d’accusé de réception**: CONTRL, 997 et schéma TA1 dans `Microsoft.BizTalk.Edi.BaseArtifacts.dll`.  
  
 Les schémas dans `Microsoft.BizTalk.Edi.BaseArtifacts.dll` sont automatiquement déployés par le programme d'installation. Ces schémas sont répertoriées dans le **schémas** nœud de la **Application EDI BizTalk** dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
 Pour utiliser les schémas de message, installez-les sur le disque dur de votre serveur en  exécutant le fichier à extraction automatique MicrosoftEdiXSDTemplates.exe dans le dossier  [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI, puis déployez-les dans votre projet dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
 **Détermination du schéma**  
  
 Lorsque le pipeline de réception EDI traite un message de réception, il détermine l'espace de noms du schéma à utiliser en traitant le message via l'accord de partenariat commercial et la  détection de schéma. Pour plus d’informations, consultez [résolution de l’accord, détection de schéma et l’autorisation pour les Messages EDI reçus](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).  
  
 Lorsque le pipeline d'envoi EDI crée un message à envoyer, il utilise les propriétés d'accord pour renseigner l'enveloppe, puis exécute la validation du schéma des informations dans les  documents informatisés. Après le chargement du schéma, le pipeline d'envoi valide le schéma par rapport aux propriétés de l'accord (ou de l'accord de secours si aucun accord n'a été désigné). En cas de validation du schéma, le pipeline valide les documents informatisés par rapport au schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [Validation des messages EDI](../core/edi-message-validation.md)
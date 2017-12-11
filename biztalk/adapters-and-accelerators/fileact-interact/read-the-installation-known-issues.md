---
title: "L’installation des problèmes connus de lecture | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 245379f2-4048-4803-83ea-38dc23eb1a81
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6641e7974a0e1872b71794af6553d708e9619dd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="read-the-installation-known-issues"></a>Lecture de l’installation des problèmes connus
[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]problèmes connus ont répertoriés dans les sections suivantes.  
  
## <a name="swift-does-not-support-stress-testing-on-integration-test-bed-itb-and-swiftnet-stub-environment"></a>SWIFT ne prend pas en charge les tests de Stress sur le banc d’essai intégration (ITB) et l’environnement de SWIFTNet Stub  
 Le ITB ne fournit pas de contrat de niveau de Service (SLA) en termes de débit et ne peut pas garantir que les données sont complètement transmises ou cohérent. Vous devez le test de stress du réseau de votre implémentation de la production dans l’environnement de pilote.  
  
 En outre, vous devez vous assurer que tous les nœuds (serveurs, des lignes et la bande passante) sont configurés correctement pour éviter toute perte de données. Voici les débits d’exemple typique :  
  
-   Interagir/Fileact envoyer sous ordinateur accentuée : 20 messages par minute  
  
-   Interagir/Fileact recevoir sous ordinateur accentuée : 300-400 messages/minute  
  
 Pour plus d’informations, consultez votre documentation SWIFT.  
  
## <a name="messages-not-pushed-when-queue-is-open"></a>Messages non envoyées lors de la file d’attente est ouvert  
 Lorsque vous utilisez interagir ou FileAct Store et le mode de transfert (msng), si la session avec la file d’attente est ouverte et que les messages ne sont pas envoyées, vous devez redémarrer SNLreceiver.exe. Cela permet d’éviter un problème avec SWIFT qui peut se produire occasionnellement.  
  
## <a name="you-must-use-cdata-when-passing-characters-like--and--in-message"></a>Vous devez utiliser CDATA lors de la transmission des caractères tels que « < » et « & » dans le message  
 Le terme CDATA est utilisé sur les données de texte ne doivent pas être analysées par l’analyseur XML.  Caractères tels que « < » et « & » ne sont pas autorisés dans les éléments XML. « < » génère une erreur, car l’analyseur l’interprète comme le début d’un nouvel élément. « & » génère une erreur, car l’analyseur l’interprète comme le début d’une entité de caractère. Tous les éléments à l’intérieur d’une section CDATA sont ignoré par l’analyseur. Une section CDATA commence par «\<! [CDATA [ » et se termine par «]]\>»  
  
## <a name="you-must-use-passthrough-pipelines-with-payload-only-mode"></a>Vous devez utiliser des Pipelines Passthrough avec le Mode de charge utile uniquement  
 Si vous utilisez le mode de charge utile uniquement pour l’adaptateur InterAct, vous devez utiliser des pipelines de transfert sur l’envoi et ports de réception si vous n’utilisez pas les pipelines personnalisés.  
  
## <a name="multiple-security-contexts-not-created-swiftnet-stub-computer"></a>Plusieurs contextes de sécurité non créés (ordinateur SWIFTNet Stub)  
 Sur un ordinateur de stub SWIFTNet, plusieurs contextes de sécurité ne sont pas créés pour les ports d’envoi différents. Plusieurs contextes de sécurité sont créées sur ITB.
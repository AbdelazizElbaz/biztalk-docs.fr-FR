---
title: "Composant de Pipeline résolution de tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ad728ff-4d7c-4ab3-af0e-76006576dce5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2e1c9b95c84d82dd1d7e2538138bcb9f89b6b8a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="party-resolution-pipeline-component"></a>Composant de Pipeline résolution du tiers

## <a name="overview"></a>Vue d'ensemble
Le rôle du composant de pipeline Résolution du tiers est de mapper le certificat ou l'identificateur de sécurité de l'expéditeur vers le tiers BizTalk Server configuré correspondant.  
  
 Lorsque le composant résolution du tiers lit le message entrant, il prend deux propriétés de contexte de message comme entrée : **WindowsUser** et **SignatureCertificate**. Le **WindowsUser** propriété est remplie par l’adaptateur, ou par un composant de pipeline personnalisé, avec le nom d’utilisateur de l’expéditeur quand il peut dériver fiable les informations d’expéditeur. Le **SignatureCertificate** est remplie par l’adaptateur ou le composant de pipeline Décodeur MIME/SMIME avec l’empreinte numérique du certificat d’authentification client.  
  
 Si le message est signé, l'empreinte du certificat utilisé pour valider la signature du message entrant est alors utilisée pour consulter l'espace de stockage Configuration et déterminer à quel tiers il est associé. Si un tiers est trouvé, le SourcePartyID de ce tiers est placé dans le contexte du message en tant qu'expéditeur du message.  
  
 Pour permettre au composant de pipeline Résolution du tiers de valider un utilisateur Windows, vous devez ajouter l’alias « WindowsUser » à un tiers. Tapez « WindowsUser » dans les champs nom et qualificateur et définissez la valeur sur un nom d’utilisateur au format de \<domaine\nom d’utilisateur\> (par exemple, domaine\utilisateur). Dans un scénario autonome, la valeur WindowsUser utilisée pour configurer le tiers doit correspondre à la valeur définie par l'adaptateur de réception.  
  
 Si le message arrive sur le composant résolution du tiers avec deux propriétés sont marquées, le composant résolution du tiers tente de résoudre le tiers par le certificat (en supposant que le **résoudre le tiers par certificat** propriété est la valeur **True**). Si le tiers est résolu, le SourcePartyID de ce tiers est placé dans le contexte du message comme OriginatorPID du message si le processus hôte de l’exécution du pipeline est marqué comme **approuvé par authentification** par le pipeline. Si la résolution du tiers ne peut pas être effectuée à l'aide du certificat, la valeur OriginatorPID du message est marquée de « s-1-5-7 », qui est le SID d'un utilisateur anonyme. Pour plus d’informations sur la propriété OriginatorPID, voir [How to Secure Pipelines](../core/how-to-secure-pipelines.md).  

## <a name="resolve-the-party"></a>Résoudre le tiers  
 Le tableau ci-dessous montre comment le composant de pipeline Résolution du tiers tente de résoudre le tiers.  
  
|Par le biais du descripteur SID|Par le biais d'un certificat|WindowsUser|SignatureCertificate|Résultat|  
|------------|--------------------|-----------------|--------------------------|------------|  
|True|False|Disponible|Disponible ou non disponible|Le tiers est résolu.|  
|True|False|Non disponible|Disponible ou non disponible|Le tiers n'est pas résolu et est marqué comme anonyme.|  
|False|True|Disponible ou non disponible|Disponible ou non disponible|Le tiers n'est pas résolu et est marqué comme anonyme.|  
|True|True|Disponible|Disponible|Le tiers est résolu.|  
|True|True|Non disponible|Disponible ou non disponible|Le tiers n'est pas résolu et est marqué comme anonyme.|  
|False|False|Disponible ou non disponible|Disponible ou non disponible|Le tiers n'est pas résolu et est marqué comme anonyme.|  
  
 Pour plus d’informations sur la configuration du composant de pipeline Résolution du tiers, consultez [comment configurer le composant de Pipeline résolution tiers](../core/how-to-configure-the-party-resolution-pipeline-component.md).  
  
## <a name="see-also"></a>Voir aussi  
-  **Les propriétés de contexte du message**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]   
-  [Composants de pipeline](../core/pipeline-components.md)   
-  [Résolution de tiers personnalisée (exemple BizTalk Server)](../core/custom-party-resolution-biztalk-server-sample.md)   
-  [Authentification des messages entre les processus](../core/authentication-of-messages-between-processes.md)
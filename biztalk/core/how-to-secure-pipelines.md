---
title: "Sécurisation des Pipelines | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac3a717f-acf8-4f08-a6fb-6d1d48b5b80a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 903e9faec81ce58aac243fb7a22bac6678a81a42
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-secure-pipelines"></a>Sécurisation des pipelines

## <a name="authentication-trusted"></a>Approuvé par authentification
Ordinateurs hôtes peuvent être marquées dans la console d’administration en tant que **approuvé par authentification**. Lorsqu'un hôte est approuvé par authentification, le serveur Microsoft BizTalk Server approuve les propriétés liées à la sécurité envoyées dans le contexte d'un message à partir de cet hôte. Les propriétés relatives à la sécurité dans le contexte du message sont les **OriginatorPID**, qui correspond à la propriété de contexte de message BizTalk Server. SourcePartyID et le **OriginatorSID**, qui correspond à la propriété de contexte de message **BTS. WindowsUser**. Pour plus d’informations, consultez **propriétés de contexte de Message** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
 Un ordinateur hôte qui est marqué comme étant **approuvé par authentification** est autorisée pour indiquer que l’hôte approuvé ajoute un message à la file d’attente d’une personne autre que lui-même en tant que l’expéditeur du message. En d’autres termes, les hôtes qui ne sont pas marqués en tant que **approuvé par authentification** ne sont pas autorisés pour ajouter un message à la file d’attente d’un expéditeur de message autres qu’eux-mêmes.  
  
> [!IMPORTANT]
>  Le composant de pipeline Décodeur MIME/SMIME ne vérifie pas la date d'expiration des certificats de déchiffrement. Toutefois, il vérifie celle des certificats de signature.  
  
 Pour plus d’informations sur le codage et décodage des messages envoyés via SMTP ou HTTP, consultez [composant de Pipeline encodeur MIME-SMIME](../core/mime-smime-encoder-pipeline-component.md). Consultez également [composant de Pipeline décodeur MIME-SMIME](../core/mime-smime-decoder-pipeline-component.md).  
  
 Pour plus d’informations sur la vérification de signature lors de la communication avec des tiers, consultez [composant de Pipeline résolution tiers](../core/party-resolution-pipeline-component.md). Consultez également [la création d’un accord](http://msdn.microsoft.com/library/f8608cf7-8ac5-4f02-805e-5a0bdf19ca8c).  
  
## <a name="see-also"></a>Voir aussi  
 [Création de Pipelines à l’aide du Concepteur de Pipeline](../core/creating-pipelines-using-pipeline-designer.md)   
 [Développement de composants de Pipeline personnalisé](../core/developing-custom-pipeline-components.md)
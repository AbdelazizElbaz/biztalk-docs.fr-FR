---
title: ValidationAdapter | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5fe99350-14c0-4ddb-b257-af9a0c4258f6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3fd80934cef17f930f5dc587bbdbf3f4b87c67e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validationadapter"></a>ValidationAdapter
L’exemple ValidationAdapter montre comment exécuter des règles de validation spéciales sur un message dans un processus public répondeur. [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] en mode natif effectue la validation de l’envoi ou réception de pipeline et dans les orchestrations. Si vous souhaitez effectuer une validation supplémentaire, vous pouvez créer un adaptateur de validation. La validation supplémentaire peut inclure la validation de champ croisé ou des règles de validation spécifique à l’entreprise que vous ne pouvez pas implémenter à l’aide d’un fichier XSD.  
  
 Vous pouvez créer un adaptateur de validation en ajoutant [!INCLUDE[btsCSharp](../../includes/btscsharp-md.md)] code à l’exemple ValidationAdapter, les interfaces de publication et en entrant la carte dans les propriétés de l’accord. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]appelle ensuite l’adaptateur de validation lors du traitement du message.  
  
 Étant donné que le ValidationAdapter est utilisé par l’orchestration de processus public, il s’exécute sous les mêmes informations d’identification que le service d’hôte BizTalk qui héberge cette orchestration.  
  
 L’exemple de ValidationAdapter se trouve dans \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for RosettaNet\SDK\ValidationAdapter.  
  
## <a name="demonstrates"></a>Montre  
 L’exemple ValidationAdapter illustre la validation de l’adresse de messagerie dans le contenu du service. L’exemple implémente la `IValidateRNIFMessageParts` interface. Elle retourne un `RNIFException` si l’adresse de messagerie n’est pas dans le format correct. Les documents XML **preambleToValidate**, **serviceHeaderToValidate**, **deliveryHeaderToValidate**, et **serviceContentToValidate**définir la validation.  
  
 Le ValidationAdapter utilise la propriété RNIFerror.IsOkToSendException pour déterminer le type de message à envoyer en cas d’erreur. Si la validation ne réussit pas, le ValidationAdapter définit RNIFerror.ErrorCode sur une valeur différente de zéro. Si la propriété de RNIFerror.IsOkToSendException est true, le processus envoie un accusé de réception négatif. Pour RNIF 2.0, il s’agit d’un message d’exception. Pour RNIF 1.1, il s’agit d’un message d’exception reçu d’accusé de réception. Si la propriété RNIFerror.IsOkToSendException est false et 0 a 1 est configuré, le processus envoie un message de 0 a 1. Une fois le processus envoie un message d’exception, message d’exception reçu d’accusé de réception ou 0 a 1 message, il va se terminer.  
  
 Si la propriété RNIFerror.IsOkToSendException est false et 0 a 1 n’est pas configuré, le processus envoie une exception, ni un 0 a 1. Il sera enregistrer l’erreur, puis se ferme.  
  
 Si la validation réussit, le ValidationAdapter définit RNIFerror.ErrorCode à 0 et BTARN achemine le message vers le processus privé. Il achemine le message vers le processus privé uniquement si la validation est réussie.  
  
## <a name="to-implement-this-sample"></a>Pour implémenter cet exemple  
 Pour implémenter l’exemple ValidationAdapter, vous devez ajouter l’adaptateur de validation de l’accord.  
  
#### <a name="to-add-the-validation-adapter-to-the-agreement"></a>Pour ajouter l’adaptateur de validation de l’accord  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
2.  Dans le [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Management Console, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur **accords**.  
  
3.  Double-cliquez sur l’accord auquel vous souhaitez ajouter l’adaptateur de validation.  
  
4.  Dans le **Validation adaptateur** boîte de dialogue, cliquez sur le bouton de sélection (**...** ) situé à droite de **nom de l’Assembly**, accédez à l’emplacement qui contient l’assembly d’adaptateur de validation, sélectionnez le fichier .dll approprié, puis cliquez sur **ouvrir**.  
  
5.  Cliquez sur la flèche vers le bas pour **nom de la classe**, sélectionnez la classe d’adaptateur de validation, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)
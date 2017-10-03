---
title: "Étape 4 : Création du projet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d88b1407-ecdd-4dbf-90da-02dc4781568c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f1d6fa03b4a686537ef04f0121c1ae168e525ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-build-the-project"></a>Étape 4 : Création du projet
![Étape 4 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-4of4.gif "Step_4of4")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous compilez le projet d’orchestration BizTalk.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir terminé [étape 3 : envoyer le Message de demande pour insérer des enregistrements et de recevoir une réponse](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md).  
  
### <a name="to-build-the-biztalk-orchestration-project"></a>Pour générer le projet d’orchestration BizTalk  
  
1.  Dans l’Explorateur de solutions, cliquez sur le nom de projet BizTalk, puis cliquez sur **propriétés**.  
  
2.  Dans la boîte de dialogue pages de propriété, dans le volet d’arborescence, développez **propriétés communes**, cliquez sur **Assembly**, puis, dans la liste des propriétés, cliquez sur le **fichier de clé d’Assembly** points de suspension **[...]** .  
  
3.  Spécifiez un chemin d’accès au fichier de clé d’assembly vous avez créé comme décrit dans [conditions préalables requises pour créer des applications SQL à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md), puis cliquez sur **ouvrir**.  
  
4.  Dans la boîte de dialogue pages de propriété, dans le volet d’arborescence, développez **propriétés de Configuration**, cliquez sur **déploiement**, puis procédez comme suit :  
  
    1.  Pour le **nom de l’Application** , tapez `SampleApplication`.  
  
    2.  Pour le **redéployer** propriété, sélectionnez **True**.  
  
     Cliquez sur **OK**.  
  
5.  Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.  
  
6.  Dans l’Explorateur de solutions, cliquez sur le nom de la solution, puis cliquez sur **générer la Solution**.  
  
     Le volet de sortie en bas de l’écran doit lire : **générer : 3 a réussi ou est à jour, 0 a échoué, 0 a été ignoré.**  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Dans cette étape, vous avez compilé la solution contenant le projet BizTalk et deux projets de bibliothèque de classes.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous déployez la solution, comme décrit dans [leçon 5 : déployer la Solution](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Envoyer le Message de demande d’insérer des enregistrements et de recevoir une réponse](../../adapters-and-accelerators/adapter-sql/step-3-send-the-request-message-to-insert-records-and-receive-a-response.md)   
 [Leçon 4 : Effectuer une opération d’insertion sur la Table de commande d’achat](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)
---
title: "Étape 3 : Configurer et démarrer l’Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4252470-805e-404f-80d5-df8d1ff3af63
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96f26035094ee6e39b672b480525747f8aaf4ede
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-configure-and-start-the-application"></a>Étape 3 : Configurer et démarrer l’Application
![Étape 3 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-3of4.gif "Step_3of4")  
  
 **Durée :** 10 minutes  
  
 **Objectif :** dans cette étape, configurer et démarrer l’application SampleApplication. Lorsque vous configurez l’application SampleApplication, vous associez les artefacts logiques que vous avez créé dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] avec leurs équivalents physiques.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir terminé [étape 2 : configurer les Ports](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md).  
  
### <a name="to-configure-and-start-the-application"></a>Pour configurer et démarrer l’application  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console sur le côté gauche, développez **Administration de BizTalk Server**, avec le bouton droit **groupe BizTalk**, puis cliquez sur **Actualiser**.  
  
3.  Développez **groupe BizTalk**, développez **Applications**, avec le bouton droit **SampleApplication**, puis cliquez sur **configurer**.  
  
4.  Dans le **configurer l’Application** boîte de dialogue le **EmployeeOrch** onglet, procédez comme suit :  
  
    1.  Pour **hôte** la liste déroulante, sélectionnez **BizTalkServerApplication**.  
  
    2.  Double-cliquez sur la cellule entre **ReceiveNotification** et sélectionnez **NotifyReceivePort** dans la liste déroulante.  
  
    3.  Double-cliquez sur la cellule entre **SQLOutboundPort** et sélectionnez **SQLOutboundPort** dans la liste déroulante.  
  
    4.  Double-cliquez sur la cellule entre **SaveResponsePort** et sélectionnez **EmailResponse** dans la liste déroulante.  
  
5.  La figure suivante illustre une application configurée.  
  
     ![Application configurée](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-011-configure-app.gif "sql_adap_tut_011_configure_app")  
  
6.  Dans le **configurer l’Application** boîte de dialogue, cliquez sur **OK**.  
  
7.  Dans l’arborescence de la console, cliquez sur **SampleApplication**, puis cliquez sur **Démarrer**.  
  
8.  Dans l’arborescence de la console, cliquez sur **Applications**.  
  
9. Dans le volet détails, vérifiez que le **état** de **SampleApplication** est **démarré**.  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Vous avez configuré et démarré l’application SampleApplication  
  
## <a name="next-steps"></a>Étapes suivantes  
 Test de l’application en insérant de nouveaux employés dans le **employé** table, comme décrit dans [étape 4 : tester l’Application](../../adapters-and-accelerators/adapter-sql/step-4-test-the-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Configurer les Ports](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-ports.md)   
 [Étape 4 : Tester l’Application](../../adapters-and-accelerators/adapter-sql/step-4-test-the-application.md)   
 [Leçon 5 : Déployer la Solution](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)
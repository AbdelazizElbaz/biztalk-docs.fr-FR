---
title: "Étape 9 : Démarrer l’Orchestration Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: private process tutorial, starting orchestrations
ms.assetid: df3ff90b-5a9f-4ae7-819a-11cb36d64ccd
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d58d7f2f9d725fca94eb6cf3d2412b3c376fe015
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-9-starting-the-contoso-orchestration"></a>Étape 9 : Démarrer l’Orchestration Contoso
Dans cette étape, vous effectuez le processus de configuration des ports en définissant les emplacements source et de destination physiques. Vous liez les ports physiques aux ports logiques que vous avez créé dans [étape 7 : création et configuration de Ports](../../adapters-and-accelerators/accelerator-rosettanet/step-7-creating-and-configuring-ports.md). Vous inscrivez ensuite le service pour associer le processus d'entreprise créé dans l'orchestration à l'environnement physique dans lequel l'orchestration doit s'exécuter. Enfin, vous démarrez l'orchestration pour qu'elle puisse participer à des transactions commerciales avec Fabrikam.  
  
### <a name="to-bind-the-orchestration-ports"></a>Pour lier les ports d'orchestration  
  
1.  Ouvrez l' **Explorateur BizTalk**.  
  
2.  Dans l'Explorateur BizTalk, développez **Base de données de configuration BizTalk**, **Orchestrations**, cliquez avec le bouton droit sur **ContosoPriceAndAvailability.PrivateResponderProcess**, puis cliquez sur **Lier**.  
  
3.  Dans la page de propriétés des liaisons de port, sélectionnez **LOB_To_PrivateResponder** dans la propriété **FromLOB** .  
  
4.  Dans la zone **ContosoSQLReqResponsePort** , sélectionnez **3A2SQLReqResponseSendPort**.  
  
5.  Dans la propriété **ToLOB** , développez **Ports d'envoi** , puis sélectionnez **PrivateResponder_To_LOB**.  
  
6.  Dans la fenêtre de configuration du volet gauche, sélectionnez **Hôte**.  
  
7.  Dans la propriété **Hôte** , dans la catégorie **Hôte BizTalk** , sélectionnez **BizTalkServerApplication** dans la liste déroulante, puis cliquez sur **OK**.  
  
### <a name="to-start-the-biztalk-runtime-process"></a>Pour démarrer le processus d'exécution BizTalk  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans la Console Administration de BizTalk, dans le volet gauche, développez [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis Développez **Instances d’hôte**.  
  
3.  Vérifiez que l'état du service **BizTalkServerApplication** est **En cours d'exécution**.  
  
### <a name="to-enlist-and-start-the-orchestration"></a>Pour inscrire et démarrer l'orchestration  
  
1.  Dans le volet gauche de la console Administration de BizTalk, développez **Applications**, **BizTalk Application 1**, puis cliquez sur **Orchestrations**.  
  
2.  Dans le volet droit, cliquez sur l'orchestration **ContosoPriceAndAvailability.PrivateResponderProcess** , puis cliquez sur **Inscrire**.  
  
3.  Cliquez avec le bouton droit sur l'orchestration **ContosoPriceAndAvailability.PrivateResponderProcess** , puis cliquez sur **Démarrer** pour démarrer l'orchestration.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de la Solution Fabrikam](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-fabrikam-solution.md)
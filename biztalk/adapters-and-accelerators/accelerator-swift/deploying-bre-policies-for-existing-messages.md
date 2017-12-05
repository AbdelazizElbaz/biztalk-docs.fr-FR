---
title: "Déploiement de stratégies BRE pour les Messages existants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 585c903d-ee44-4e92-8798-febb176367e3
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4cd094feabe1ba23a6a73c89aae3a1042b8f7fc9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="deploying-bre-policies-for-existing-messages"></a><span data-ttu-id="d2c20-102">Déploiement de stratégies BRE pour les Messages existants</span><span class="sxs-lookup"><span data-stu-id="d2c20-102">Deploying BRE Policies for Existing Messages</span></span>
<span data-ttu-id="d2c20-103">**Pour déployer des règles métier connexes :**</span><span class="sxs-lookup"><span data-stu-id="d2c20-103">**To deploy the related business rules:**</span></span>  
  
1.  <span data-ttu-id="d2c20-104">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft BizTalk Accelerator pour SWIFT**, puis cliquez sur **l’utilitaire de déploiement BRE**.</span><span class="sxs-lookup"><span data-stu-id="d2c20-104">Click **Start**, click **Programs**, click **Microsoft BizTalk Accelerator for SWIFT**, and then click **BRE Deployment Utility**.</span></span>  
  
2.  <span data-ttu-id="d2c20-105">Dans l’utilitaire de déploiement BRE, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="d2c20-105">In BRE Deployment Utility, click **Browse**.</span></span>  
  
3.  <span data-ttu-id="d2c20-106">Dans la boîte de dialogue .NET Global Assembly Cache, sélectionnez **SWIFT MX schéma**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d2c20-106">In the .NET Global Assembly Cache dialog box, select **SWIFT MX Schema**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="d2c20-107">Cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="d2c20-107">Click **Deploy**.</span></span>  
  
     <span data-ttu-id="d2c20-108">Selon les schémas déployés avec cet assembly, l’utilitaire de déploiement identifie les règles associées et les publie pour une utilisation avec le moteur BRE.</span><span class="sxs-lookup"><span data-stu-id="d2c20-108">Based on the schemas deployed with that assembly, the deployment utility identifies the related rules and publishes them for use with the BRE.</span></span> <span data-ttu-id="d2c20-109">Lorsque vous avez terminé, l’utilitaire de déploiement du moteur BRE affiche le message suivant : « déploiement s’est terminée.</span><span class="sxs-lookup"><span data-stu-id="d2c20-109">When complete, the BRE Deployment Utility displays the following message: "Deployment has completed.</span></span> <span data-ttu-id="d2c20-110">Afficher le fichier journal ou l’éditeur des règles d’entreprise pour plus d’informations. »</span><span class="sxs-lookup"><span data-stu-id="d2c20-110">View the log file or Business Rules Composer for details."</span></span>  
  
5.  <span data-ttu-id="d2c20-111">Fermez la boîte de dialogue Utilitaire de déploiement BRE SWIFT.</span><span class="sxs-lookup"><span data-stu-id="d2c20-111">Close the SWIFT BRE Deployment Utility dialog box.</span></span>  
  
6.  <span data-ttu-id="d2c20-112">Dans l’Explorateur Windows, accédez à  *\<lecteur\>*: \Documents and Settings\All Users\Application Data pour vérifier que le fichier journal BREDeploymentLog.txt figure dans le dossier.</span><span class="sxs-lookup"><span data-stu-id="d2c20-112">In Windows Explorer, browse to *\<drive\>*:\Documents and Settings\All Users\Application Data to confirm that the log file BREDeploymentLog.txt appears in the folder.</span></span>  
  
7.  <span data-ttu-id="d2c20-113">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **services.msc**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d2c20-113">Click **Start**, click **Run**, type **services.msc**, and then click **OK**.</span></span> <span data-ttu-id="d2c20-114">Dans la fenêtre Services (Local), cliquez sur **Service de mise à jour du moteur de règles**, puis cliquez sur **redémarrer**.</span><span class="sxs-lookup"><span data-stu-id="d2c20-114">In the Services (Local) window, right-click **Rule Engine Update Service**, and then click **Restart**.</span></span>
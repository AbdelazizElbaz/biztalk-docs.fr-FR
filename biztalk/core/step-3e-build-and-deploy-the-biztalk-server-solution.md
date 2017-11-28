---
title: "Étape 3e : générer et déployer la Solution BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbfc382b-ed4a-4401-9343-be1bffd747c9
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a970a8f7adb450156b89849eb986c84fd05ab55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3e-build-and-deploy-the-biztalk-server-solution"></a><span data-ttu-id="adb77-102">Étape 3e : générer et déployer la Solution BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="adb77-102">Step 3e: Build and Deploy the BizTalk Server Solution</span></span>
<span data-ttu-id="adb77-103">Dans cette rubrique, nous allons déployer les deux [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projets (**BtsSalesforceIntegration** et **CustomPipeline**) que vous avez créée aux étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="adb77-103">In this topic, we’ll deploy the two [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projects (**BtsSalesforceIntegration** and **CustomPipeline**) that we created in the earlier steps.</span></span>  
  
### <a name="to-build-and-deploy-the-biztalk-server-projects"></a><span data-ttu-id="adb77-104">Pour générer et déployer des projets BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="adb77-104">To build and deploy the BizTalk Server projects</span></span>  
  
1.  <span data-ttu-id="adb77-105">Dans l’Explorateur de solutions, cliquez sur le **BtsSalesforceIntegration** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="adb77-105">In the Solution Explorer, right-click the **BtsSalesforceIntegration**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="adb77-106">Dans le **déploiement** onglet, pour **nom de l’Application**, entrez **SalesforceIntegration**.</span><span class="sxs-lookup"><span data-stu-id="adb77-106">In the **Deployment** tab, for **Application Name**, enter **SalesforceIntegration**.</span></span> <span data-ttu-id="adb77-107">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="adb77-107">Click **Save**.</span></span>  
  
3.  <span data-ttu-id="adb77-108">Avec le bouton droit de la même façon, le **CustomPipeline** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de projet, cliquez sur **propriétés**et dans le **déploiement** onglet, pour le **Application Nom** propriété, entrez **SalesforceIntegration** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="adb77-108">Similarly, right-click the **CustomPipeline**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project, click **Properties**, and in the **Deployment** tab, for the **Application Name** property, enter **SalesforceIntegration** again.</span></span> <span data-ttu-id="adb77-109">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="adb77-109">Click **Save**.</span></span> <span data-ttu-id="adb77-110">Cela garantit que le composant de pipeline personnalisé est déployé dans la même application que le **BtsSalesforceIntegration** projet.</span><span class="sxs-lookup"><span data-stu-id="adb77-110">This ensures that the custom pipeline component is deployed to the same application as the **BtsSalesforceIntegration** project.</span></span>  
  
4.  <span data-ttu-id="adb77-111">Cliquez sur le nom de la solution dans l’Explorateur de solutions, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="adb77-111">Right-click the solution name in the Solution Explorer, and click **Properties**.</span></span> <span data-ttu-id="adb77-112">Dans la boîte de dialogue Pages de propriétés de Solution, cliquez sur **propriétés de Configuration**et vérifiez que le **générer** et **déployer** cases à cocher sont activées à la fois pour **BtsSalesforceIntegration** et **CustomPipeline** projets.</span><span class="sxs-lookup"><span data-stu-id="adb77-112">In the Solution Property Pages dialog box, click **Configuration Properties**, and verify that the **Build** and **Deploy** check boxes are selected both for **BtsSalesforceIntegration** and **CustomPipeline** projects.</span></span>  
  
5.  <span data-ttu-id="adb77-113">Cliquez sur le nom de la solution dans l’Explorateur de solutions, puis cliquez sur **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="adb77-113">Right-click the solution name in the Solution Explorer and then click **Build Solution**.</span></span> <span data-ttu-id="adb77-114">Une fois la solution générée avec succès, cliquez à nouveau sur le nom de la solution, puis cliquez sur **déployer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="adb77-114">After the solution builds successfully, right-click the solution name again, and then click **Deploy Solution**.</span></span> <span data-ttu-id="adb77-115">La solution est déployée dans la console d'administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="adb77-115">The solution is deployed to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adb77-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adb77-116">See Also</span></span>  
 [<span data-ttu-id="adb77-117">Étape 3 : Créer la Solution BizTalk Server dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="adb77-117">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)
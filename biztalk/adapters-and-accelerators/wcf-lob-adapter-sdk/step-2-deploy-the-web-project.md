---
title: "Étape 2 : Déployer le projet Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb775a89-2e2d-43e5-94ae-f75c1756dbd7
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85cef88de4e8fa05bb50840002a0f344b1f0b350
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2017
---
# <a name="step-2-deploy-the-web-project"></a><span data-ttu-id="a6e57-102">Étape 2 : Déployer le projet Web</span><span class="sxs-lookup"><span data-stu-id="a6e57-102">Step 2: Deploy the Web Project</span></span>
<span data-ttu-id="a6e57-103">![Étape 2 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span><span class="sxs-lookup"><span data-stu-id="a6e57-103">![Step 2 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span></span>  
  
 <span data-ttu-id="a6e57-104">**Durée :** 5 minutes</span><span class="sxs-lookup"><span data-stu-id="a6e57-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="a6e57-105">Dans cette étape, vous allez publier le projet Web généré dans [étape 1 : utiliser l’Assistant développement d’adaptateurs pour créer le projet Web](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md) pour Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="a6e57-105">In this step you will publish the Web project generated in [Step 1: Use the Adapter Service Development Wizard to Create the Web Project](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md) to Internet Information Services (IIS).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a6e57-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a6e57-106">Prerequisites</span></span>  
 <span data-ttu-id="a6e57-107">Pour effectuer cette étape, vous devez avoir terminé [étape 1 : utiliser l’Assistant développement d’adaptateurs pour créer le projet Web](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md).</span><span class="sxs-lookup"><span data-stu-id="a6e57-107">To complete this step, you should have completed [Step 1: Use the Adapter Service Development Wizard to Create the Web Project](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md).</span></span> <span data-ttu-id="a6e57-108">Votre serveur Web doit avoir également un certificat SSL installé pour permettre une communication HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a6e57-108">Your Web server must also have an SSL certificate installed to enable HTTPS communication.</span></span>  
  
## <a name="compile-and-deploy-the-web-project"></a><span data-ttu-id="a6e57-109">Compilez et déployez le projet Web</span><span class="sxs-lookup"><span data-stu-id="a6e57-109">Compile and deploy the Web project</span></span>  
  
1.  <span data-ttu-id="a6e57-110">Dans Visual Studio, chargez le projet de EchoWeb créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="a6e57-110">In Visual Studio, load the EchoWeb project created previously.</span></span>  
  
2.  <span data-ttu-id="a6e57-111">Ouvrez une invite de commandes Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a6e57-111">Open a Visual Studio command prompt.</span></span>  
  
3.  <span data-ttu-id="a6e57-112">À l’invite de commandes, à partir du dossier C:\tutorials\echoweb, tapez la commande suivante et appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="a6e57-112">At the command prompt, from the C:\tutorials\echoweb folder, type the following command, and then press ENTER:</span></span>  
  
     <span data-ttu-id="a6e57-113">**sn /k EchoWebKey.snk**</span><span class="sxs-lookup"><span data-stu-id="a6e57-113">**sn /k EchoWebKey.snk**</span></span>  
  
     <span data-ttu-id="a6e57-114">Un message de confirmation, **écrites dans EchoWebKey.snk de paire de clés**, affiche sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a6e57-114">A confirmation message, **Key pair written to EchoWebKey.snk**, displays on the command line.</span></span>  
  
4.  <span data-ttu-id="a6e57-115">Fermez l'invite de commande.</span><span class="sxs-lookup"><span data-stu-id="a6e57-115">Close the command prompt.</span></span>  
  
5.  <span data-ttu-id="a6e57-116">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet EchoWeb, puis sélectionnez **publier le Site Web**.</span><span class="sxs-lookup"><span data-stu-id="a6e57-116">In **Solution Explorer**, right click the EchoWeb project, and then select **Publish Web Site**.</span></span>  
  
6.  <span data-ttu-id="a6e57-117">Dans le **publier le Site Web** boîte de dialogue, pour **emplacement cible**, entrez **http://machinename/EchoWeb**.</span><span class="sxs-lookup"><span data-stu-id="a6e57-117">In the **Publish Web Site** dialog box, for **Target location**, enter **http://machinename/EchoWeb**.</span></span> <span data-ttu-id="a6e57-118">Sélectionnez **autoriser ce site précompilé à être mis à jour**, **utiliser fixe pour les assemblys d’affectation de noms et une page**, et **activer de noms forts sur les assemblys précompilés**.</span><span class="sxs-lookup"><span data-stu-id="a6e57-118">Select **Allow this precompiled site to be updatable**, **Use fixed naming and single page assemblies**, and **Enable strong naming on precompiled assemblies**.</span></span> <span data-ttu-id="a6e57-119">Dans le **emplacement du fichier de clé** , cliquez sur le bouton de sélection **(...)**  bouton, sélectionnez le fichier EchoWebKey.snk créé précédemment, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a6e57-119">In the **Key file location** field, click the ellipsis **(…)** button, select the EchoWebKey.snk file created previously, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="a6e57-120">Pour vérifier que le site Web a été correctement créé, démarrez Internet Explorer, entrez **« http://localhost/EchoWeb/EchoOutboundContract.svc »** dans la barre d’adresses et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="a6e57-120">To verify that the Web site was correctly created, start Internet Explorer, enter  **"http://localhost/EchoWeb/EchoOutboundContract.svc"** in the address bar, and then press ENTER.</span></span> <span data-ttu-id="a6e57-121">Une page Web qui décrit le EchoOutboundContractClient doit apparaître.</span><span class="sxs-lookup"><span data-stu-id="a6e57-121">A Web page that describes the EchoOutboundContractClient should appear.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="a6e57-122">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="a6e57-122">What did I just do?</span></span>  
 <span data-ttu-id="a6e57-123">Vous venez de publier votre projet Web pour IIS.</span><span class="sxs-lookup"><span data-stu-id="a6e57-123">You have just published your Web project to IIS.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a6e57-124">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a6e57-124">Next Steps</span></span>  
 <span data-ttu-id="a6e57-125">Maintenant que vous avez compilé et déployé le projet, vous pouvez passer à [étape 3 : créer un fichier de définition d’Application](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md)</span><span class="sxs-lookup"><span data-stu-id="a6e57-125">Now that you have compiled and deployed the project, you can proceed to [Step 3: Create an Application Definition File](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e57-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6e57-126">See Also</span></span>  
 [<span data-ttu-id="a6e57-127">Didacticiel 3 : Hébergement de l’adaptateur Echo dans IIS</span><span class="sxs-lookup"><span data-stu-id="a6e57-127">Tutorial 3: Hosting the Echo Adapter in IIS</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)
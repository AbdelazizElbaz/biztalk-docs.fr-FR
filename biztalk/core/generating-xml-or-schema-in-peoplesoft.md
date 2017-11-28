---
title: "Génération XML ou schéma dans PeopleSoft | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating schemas
- schemas, generating
- generating XML
- XML, generating
ms.assetid: adfe2936-0dc2-42d2-b26a-718f8cc57eff
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a7fbd164f7c0d380f6ee0c0fda59098203f7585
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generating-xml-or-schema-in-peoplesoft"></a><span data-ttu-id="465b0-102">Génération de code XML ou de schémas dans PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="465b0-102">Generating XML or Schema in PeopleSoft</span></span>
<span data-ttu-id="465b0-103">La procédure suivante explique comment utiliser PeopleSoft Enterprise pour créer un fichier XML et déclencher un événement PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="465b0-103">The following procedure describes how to use PeopleSoft Enterprise to create an XML file and trigger a PeopleSoft event.</span></span> <span data-ttu-id="465b0-104">Pour cela, vous devez modifier l'environnement PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="465b0-104">To do this, you change something in the PeopleSoft environment.</span></span> <span data-ttu-id="465b0-105">La modification active un fichier XML qui est envoyé au dossier dont vous définissez dans votre orchestration qu'il doit être surveillé.</span><span class="sxs-lookup"><span data-stu-id="465b0-105">The change activates an XML file, which is sent to the file folder that you set in your orchestration to be monitored.</span></span> <span data-ttu-id="465b0-106">Vous importez ensuite le fichier XML dans BizTalk Server et vous générez un schéma.</span><span class="sxs-lookup"><span data-stu-id="465b0-106">Later, in BizTalk Server, you import the XML and generate a schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="465b0-107">Lorsque vous associez l'emplacement au nœud MSEXTERNAL, tous les changements apportés à la valeur d'emplacement génèrent un document XML, ce qui déclenche un événement.</span><span class="sxs-lookup"><span data-stu-id="465b0-107">When you associate the Location with the MSEXTERNAL node, any change made to Location Value generates an XML document—triggering an event.</span></span> <span data-ttu-id="465b0-108">Après avoir inscrit et démarré votre orchestration, vous pouvez parcourir les écrans PeopleSoft jusqu'à l'écran LOCATION.</span><span class="sxs-lookup"><span data-stu-id="465b0-108">After enlisting and starting your orchestration, you can navigate through the PeopleSoft screens to the LOCATION screen.</span></span> <span data-ttu-id="465b0-109">Si vous modifiez la valeur de l'emplacement et que vous enregistrez cette modification, un fichier XML correspondant s'affiche dans votre répertoire \out.</span><span class="sxs-lookup"><span data-stu-id="465b0-109">If you make a change to Location Value and save your change, a corresponding XML appears in your \out directory.</span></span>  
  
### <a name="to-generate-xml-or-schema-in-peoplesoft"></a><span data-ttu-id="465b0-110">Pour générer un fichier XML ou un schéma XSD dans PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="465b0-110">To generate XML or Schema in PeopleSoft</span></span>  
  
1.  <span data-ttu-id="465b0-111">Dans l’application PeopleSoft, pointez sur **configurer l’aspect financier**, pointez sur **chaîne logistique**, pointez sur **des définitions communes**, pointez sur **emplacement**, puis sélectionnez **emplacement**.</span><span class="sxs-lookup"><span data-stu-id="465b0-111">In the PeopleSoft application, point to **Set up Financials**, point to **Supply Chain**, point to **Common Definitions**, point to **Location**, and then select **Location**.</span></span>  
  
2.  <span data-ttu-id="465b0-112">Sur le **emplacement** écran, entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="465b0-112">On the **Location** screen, enter the following information:</span></span>  
  
    -   <span data-ttu-id="465b0-113">**ID de l’ensemble :** entrez **partage**.</span><span class="sxs-lookup"><span data-stu-id="465b0-113">**Set ID:** Enter **SHARE**.</span></span>  
  
    -   <span data-ttu-id="465b0-114">**Code de l’emplacement :** entrer un code qui commence par `WKLOC`.</span><span class="sxs-lookup"><span data-stu-id="465b0-114">**Location Code:** Enter a code that starts with `WKLOC`.</span></span>  
  
     ![](../core/media/psadapter-18-task-sharesearch.gif "PSAdapter_18_Task_ShareSearch")  
  
3.  <span data-ttu-id="465b0-115">Cliquez sur **recherche**, puis cliquez sur **historique des corrections** à placer l’écran en **modifier** mode.</span><span class="sxs-lookup"><span data-stu-id="465b0-115">Click **Search**, and then click **Correct History** to put the screen in **Edit** mode.</span></span>  
  
     ![](../core/media/psadapter-19-task-correcthistory.gif "PSAdapter_19_Task_CorrectHistory")  
  
4.  <span data-ttu-id="465b0-116">Apportez une modification à un champ à l’écran, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="465b0-116">Make a change to a field on the screen, and then click **Save**.</span></span>  
  
5.  <span data-ttu-id="465b0-117">Pointez sur **PeopleTools**, pointez sur **Integration Broker**, pointez sur **moniteur**, puis sélectionnez **surveiller le Message**.</span><span class="sxs-lookup"><span data-stu-id="465b0-117">Point to **PeopleTools**, point to **Integration Broker**, point to **Monitor**, and then select **Monitor Message**.</span></span>  
  
     ![](../core/media/psadapter-20-task-monitormessage.gif "PSAdapter_20_Task_MonitorMessage")  
  
6.  <span data-ttu-id="465b0-118">Assurez-vous que **Type de canal** est **Message d’Instance**, puis cliquez sur **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="465b0-118">Make sure that **Channel Type** is **Message Instance**, and then click **Refresh**.</span></span>  
  
7.  <span data-ttu-id="465b0-119">Dans le **fait** colonne, cliquez sur le numéro.</span><span class="sxs-lookup"><span data-stu-id="465b0-119">In the **Done** column, click the number.</span></span>  
  
8.  <span data-ttu-id="465b0-120">Faites défiler vers le bas de la liste et cliquez sur le **détails** lien sur un **LOCATION_SYNC** message.</span><span class="sxs-lookup"><span data-stu-id="465b0-120">Scroll to the bottom of the list and click the **Details** link on a **LOCATION_SYNC** message.</span></span>  
  
     ![](../core/media/psadapter-21-task-detailslink.gif "PSAdapter_21_Task_DetailsLink")  
  
9. <span data-ttu-id="465b0-121">Cliquez sur **afficher XML** sur un **MSEXTERNAL** nœud.</span><span class="sxs-lookup"><span data-stu-id="465b0-121">Click **View XML** on a **MSEXTERNAL** Node.</span></span>  
  
     ![](../core/media/psadapter-22-task-viewxml.gif "PSAdapter_22_Task_ViewXML")  
  
     <span data-ttu-id="465b0-122">Copiez et collez le contenu du fichier XML dans un fichier accessible depuis votre projet BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="465b0-122">Copy and paste the contents of the XML into a file that can be accessed by your BizTalk Server project.</span></span>  
  
     ![](../core/media/psadapter-23-task-xmlresult.gif "PSAdapter_23_Task_XMLResult")  
  
10. <span data-ttu-id="465b0-123">Mémorisez l'emplacement du fichier pour le référencer dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="465b0-123">Remember the location of the file;  you reference it in BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="465b0-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="465b0-124">See Also</span></span>  
 [<span data-ttu-id="465b0-125">Annexe b : à l’aide de l’Application PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="465b0-125">Appendix B: Using the PeopleSoft Application</span></span>](../core/appendix-b-using-the-peoplesoft-application.md)
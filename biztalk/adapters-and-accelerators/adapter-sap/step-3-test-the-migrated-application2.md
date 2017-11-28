---
title: "Étape 3 : Tester l’Application2 migrés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migration, testing the migrated application (Send IDOC)
- migration
ms.assetid: 8dc0d127-71ce-4668-a3bf-c893a8f6848d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6dbf6154337dc9daf5dcfe75b3f5b7299ae843ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-test-the-migrated-application"></a><span data-ttu-id="bb581-102">Étape 3 : Tester l’Application migrée</span><span class="sxs-lookup"><span data-stu-id="bb581-102">Step 3: Test the Migrated Application</span></span>
<span data-ttu-id="bb581-103">![Étape 3 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span><span class="sxs-lookup"><span data-stu-id="bb581-103">![Step 3 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span></span>  
  
 <span data-ttu-id="bb581-104">**Durée :** 5 minutes</span><span class="sxs-lookup"><span data-stu-id="bb581-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="bb581-105">**Objectif :** dans cette étape, vous allez tester l’application migrée en envoyant un IDOC de fichier plat à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb581-105">**Objective:** In this step, you will test the migrated application by sending a flat-file IDOC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="bb581-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="bb581-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="bb581-107">Configurer l’application BizTalk en mappant les ports logiques de l’orchestration BizTalk aux ports physiques dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="bb581-107">Configure the BizTalk application by mapping the logical ports in the BizTalk orchestration to physical ports in the BizTalk Server Administration console.</span></span>  
  
-   <span data-ttu-id="bb581-108">Configurer l’application BizTalk à utiliser le port d’envoi WCF-custom pour la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb581-108">Configure the BizTalk application to use the WCF-custom send port for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
### <a name="to-test-the-migrated-application"></a><span data-ttu-id="bb581-109">Pour tester l’application migrée</span><span class="sxs-lookup"><span data-stu-id="bb581-109">To test the migrated application</span></span>  
  
1.  <span data-ttu-id="bb581-110">Dans le dossier SendIDOC_Migration, copiez le fichier BOMDOC.txt.</span><span class="sxs-lookup"><span data-stu-id="bb581-110">From the SendIDOC_Migration folder, copy the BOMDOC.txt file.</span></span> <span data-ttu-id="bb581-111">Il s’agit de l’IDOC de fichier plat à envoyer au système SAP.</span><span class="sxs-lookup"><span data-stu-id="bb581-111">This is the flat-file IDOC to be sent to the SAP system.</span></span>  
  
2.  <span data-ttu-id="bb581-112">Emplacement de réception de coller l’IDOC de fichier plat dans le dossier qui est mappé au fichier.</span><span class="sxs-lookup"><span data-stu-id="bb581-112">Paste the flat-file IDOC to the folder that is mapped to the file receive location.</span></span>  
  
3.  <span data-ttu-id="bb581-113">L’orchestration utilise le fichier et envoie l’IDOC au système SAP.</span><span class="sxs-lookup"><span data-stu-id="bb581-113">The orchestration consumes the file and sends the IDOC to the SAP system.</span></span> <span data-ttu-id="bb581-114">Vérifiez s’il existe des erreurs dans l’Observateur d’événements.</span><span class="sxs-lookup"><span data-stu-id="bb581-114">Verify if there are any errors in the event viewer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb581-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb581-115">See Also</span></span>  
 [<span data-ttu-id="bb581-116">Didacticiel 3 : Migration d’un projet BizTalk SAP envoi IDOC</span><span class="sxs-lookup"><span data-stu-id="bb581-116">Tutorial 3: Migrating an SAP Send IDOC BizTalk Project</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-3-migrating-an-sap-send-idoc-biztalk-project.md)
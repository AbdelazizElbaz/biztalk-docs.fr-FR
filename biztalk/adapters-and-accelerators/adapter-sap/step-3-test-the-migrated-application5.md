---
title: "Étape 3 : Tester le Application5 migrés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migration, testing the migrated application (Receive IDOC)
- migration
ms.assetid: 3ad15069-1556-4c0a-8bfd-86704d40c586
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b5e49968e4b0b463b1665d0752689a14039c2da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-test-the-migrated-application"></a><span data-ttu-id="06a3f-102">Étape 3 : Tester l’Application migrée</span><span class="sxs-lookup"><span data-stu-id="06a3f-102">Step 3: Test the Migrated Application</span></span>
<span data-ttu-id="06a3f-103">![Étape 3 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span><span class="sxs-lookup"><span data-stu-id="06a3f-103">![Step 3 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span></span>  
  
 <span data-ttu-id="06a3f-104">**Durée :** 5 minutes</span><span class="sxs-lookup"><span data-stu-id="06a3f-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="06a3f-105">**Objectif :** dans cette étape, vous allez tester l’application migrée en recevant un IDOC de fichier plat à l’aide de la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06a3f-105">**Objective:** In this step, you will test the migrated application by receiving a flat-file IDOC using the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="06a3f-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="06a3f-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="06a3f-107">Configurer l’application BizTalk en mappant les ports logiques de l’orchestration BizTalk aux ports physiques dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="06a3f-107">Configure the BizTalk application by mapping the logical ports in the BizTalk orchestration to physical ports in the BizTalk Server Administration console.</span></span>  
  
-   <span data-ttu-id="06a3f-108">Configurer BizTalk application afin d’utiliser WCF-Custom port de réception pour la station de travail WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06a3f-108">Configure the BizTalk application to use the WCF-Custom receive port for the WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
### <a name="to-test-the-migrated-application"></a><span data-ttu-id="06a3f-109">Pour tester l’application migrée</span><span class="sxs-lookup"><span data-stu-id="06a3f-109">To test the migrated application</span></span>  
  
1.  <span data-ttu-id="06a3f-110">Démarrer l’interface GUI SAP et se connecter au système SAP que vous avez spécifié dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="06a3f-110">Start the SAP GUI, and connect to the SAP system that you specified in the connection URI.</span></span>  
  
2.  <span data-ttu-id="06a3f-111">Exécutez SE37 et appeler un module de fonction dans SAP qui envoie un IDOC à un système externe.</span><span class="sxs-lookup"><span data-stu-id="06a3f-111">Run SE37, and invoke a function module in SAP that sends an IDOC to an external system.</span></span> <span data-ttu-id="06a3f-112">Assurez-vous de qu'envoyer l’IDOC en utilisant le même ID de programme qui est spécifié dans l’URI de connexion pour le port de réception WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="06a3f-112">Make sure you send the IDOC using the same program ID that is specified in the connection URI for the WCF-Custom receive port.</span></span>  
  
3.  <span data-ttu-id="06a3f-113">Recherchez l’IDOC entrant à l’emplacement de fichier spécifié dans le cadre de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="06a3f-113">Look for the inbound IDOC at the file location specified as part of the orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06a3f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06a3f-114">See Also</span></span>  
 [<span data-ttu-id="06a3f-115">Didacticiel 4 : Migration d’un SAP de réception projet BizTalk IDOC</span><span class="sxs-lookup"><span data-stu-id="06a3f-115">Tutorial 4: Migrating an SAP Receive IDOC BizTalk Project</span></span>](../../adapters-and-accelerators/adapter-sap/tutorial-4-migrating-an-sap-receive-idoc-biztalk-project.md)
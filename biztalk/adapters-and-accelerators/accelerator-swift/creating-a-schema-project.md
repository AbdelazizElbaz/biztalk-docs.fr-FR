---
title: "Création d’un projet de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67e6278c-a597-4700-80bf-48e37aaa9c05
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58017b24f7b7464745f48cc202734217dfb327d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-schema-project"></a><span data-ttu-id="c6363-102">Création d’un projet de schéma</span><span class="sxs-lookup"><span data-stu-id="c6363-102">Creating a Schema Project</span></span>
<span data-ttu-id="c6363-103">Pour créer un projet de schéma :</span><span class="sxs-lookup"><span data-stu-id="c6363-103">To create a schema project:</span></span>  
  
1.  <span data-ttu-id="c6363-104">Dans Visual Studio, créez le projet SWIFT MX schéma BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c6363-104">In Visual Studio, create the SWIFT MX Schema BizTalk project.</span></span>  
  
2.  <span data-ttu-id="c6363-105">Ajouter le schéma MX approprié (téléchargé à partir du site de ISO20022), que vous souhaitez tester, à ce projet.</span><span class="sxs-lookup"><span data-stu-id="c6363-105">Add the appropriate MX schema (downloaded from ISO20022 site), which you wish to test, to this project.</span></span>  
  
3.  <span data-ttu-id="c6363-106">Si vous souhaitez exécuter la fonctionnalité de Message Repair et New Submission pour le message MX ci-dessus, un schéma d’enveloppe correspond également au type de message ci-dessus doit être déployé sinon passez à l’étape 6.</span><span class="sxs-lookup"><span data-stu-id="c6363-106">If you want to execute the Message Repair and New Submission functionality for the above MX message, then an Envelope schema corresponding to the above message type also needs to be deployed else proceed to step 6.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c6363-107">Pour plus d’informations sur la façon de générer des schémas d’enveloppe de MX, reportez-vous à la Documentation du Générateur de formulaire.</span><span class="sxs-lookup"><span data-stu-id="c6363-107">For information on how to generate MX Envelope schemas, please refer to the Form Generator Documentation.</span></span>  
  
4.  <span data-ttu-id="c6363-108">Ajoutez le schéma d’enveloppe pour le projet SWIFT MX schéma.</span><span class="sxs-lookup"><span data-stu-id="c6363-108">Add the Envelope schema to the SWIFT MX Schema project.</span></span>  
  
5.  <span data-ttu-id="c6363-109">Ouvrez le schéma d’enveloppe dans l’Éditeur BizTalk et promouvoir les propriétés « CorrelationToken » et « IsNewSubmission ».</span><span class="sxs-lookup"><span data-stu-id="c6363-109">Open the Envelope schema in the BizTalk editor and promote “CorrelationToken” and “IsNewSubmission” properties.</span></span> <span data-ttu-id="c6363-110">Cliquez sur les champs ci-dessus, sur **promouvoir -> Promotion rapide** pour promouvoir ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="c6363-110">Right-click the above fields and click **Promote -> Quick Promotion** to promote these properties.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c6363-111">Pour plus d’informations sur la promotion des propriétés d’un schéma, reportez-vous à la documentation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c6363-111">For more information on how to promote properties of a schema, please refer to the BizTalk Server documentation.</span></span>  
  
6.  <span data-ttu-id="c6363-112">Créer un fichier de clé (à l’aide de Sn – k key.snk), puis l’affecter au projet pour créer un nom fort nommé assembly.</span><span class="sxs-lookup"><span data-stu-id="c6363-112">Create a key file (using Sn –k key.snk), and then assign it to the project to create a strong named assembly.</span></span>  
  
7.  <span data-ttu-id="c6363-113">Générez et déployez le projet.</span><span class="sxs-lookup"><span data-stu-id="c6363-113">Build and then deploy the project.</span></span>
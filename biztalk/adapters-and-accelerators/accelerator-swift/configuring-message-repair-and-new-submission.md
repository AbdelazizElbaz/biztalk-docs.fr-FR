---
title: Configuration de Message Repair et New Submission | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Message Repair and New Submission, configuring
- A4SWIFT, Message Repair and New Submission
- configuring, Message Repair and New Submission
ms.assetid: e3e5e865-109c-469e-8b5b-c2675583d5a5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00e42bcfc5e744aa005e2e0a790dfc505b7a834d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-message-repair-and-new-submission"></a><span data-ttu-id="00574-102">Configuration de Message Repair et New Submission</span><span class="sxs-lookup"><span data-stu-id="00574-102">Configuring Message Repair and New Submission</span></span>
<span data-ttu-id="00574-103">Vous devez effectuer les étapes dans les sections suivantes pour configurer la fonctionnalité de Message Repair et New Submission de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)], comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="00574-103">You must perform the steps in the following sections to configure the Message Repair and New Submission feature of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)], as shown in the following figure.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-message-repair-configuration.gif "A4SWIFT_Message_Repair_Configuration")  
  
 <span data-ttu-id="00574-104">Dans l’Assistant Installation d’A4SWIFT, vous pouvez choisir d’installer Message Repair et New Submission et rapprochement de réponse de FIN (FRR), ou Message Repair et New Submission sans FRR ou FRR sans Message Repair et New Submission.</span><span class="sxs-lookup"><span data-stu-id="00574-104">In the A4SWIFT Installation Wizard, you can choose to install Message Repair and New Submission and FIN Response Reconciliation (FRR), or Message Repair and New Submission without FRR, or FRR without Message Repair and New Submission.</span></span> <span data-ttu-id="00574-105">Par conséquent, les instructions de cette section ne supposent pas que vous installez et configurez FRR.</span><span class="sxs-lookup"><span data-stu-id="00574-105">As a result, the instructions in this section do not assume that you are installing and configuring FRR.</span></span> <span data-ttu-id="00574-106">Ils, toutefois, supposez que vous avez effectué les étapes décrites dans le [Guide de Configuration de composants A4SWIFT](../../adapters-and-accelerators/accelerator-swift/a4swift-component-configuration-guide.md) section.</span><span class="sxs-lookup"><span data-stu-id="00574-106">They do, however, assume that you have performed the steps in the [A4SWIFT Component Configuration Guide](../../adapters-and-accelerators/accelerator-swift/a4swift-component-configuration-guide.md) section.</span></span>  
  
 <span data-ttu-id="00574-107">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="00574-107">This section contains:</span></span>  
  
-   [<span data-ttu-id="00574-108">Installation de certificats</span><span class="sxs-lookup"><span data-stu-id="00574-108">Installing Certificates</span></span>](../../adapters-and-accelerators/accelerator-swift/installing-certificates.md)  
  
-   [<span data-ttu-id="00574-109">Définition des propriétés A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="00574-109">Setting A4SWIFT Properties</span></span>](../../adapters-and-accelerators/accelerator-swift/setting-a4swift-properties.md)  
  
-   [<span data-ttu-id="00574-110">Ajout d’utilisateurs d’A4SWIFT et de mise à jour de groupes Windows</span><span class="sxs-lookup"><span data-stu-id="00574-110">Adding A4SWIFT Users and Updating Windows Groups</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-a4swift-users-and-updating-windows-groups.md)  
  
-   [<span data-ttu-id="00574-111">Ajout de rôles et services</span><span class="sxs-lookup"><span data-stu-id="00574-111">Adding Roles and Departments</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-roles-and-departments.md)  
  
-   [<span data-ttu-id="00574-112">Déploiement des schémas d’enveloppe A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="00574-112">Deploying A4SWIFT Envelope Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-envelope-schemas.md)  
  
-   [<span data-ttu-id="00574-113">Publication de modèles de formulaire InfoPath</span><span class="sxs-lookup"><span data-stu-id="00574-113">Publishing InfoPath Form Templates</span></span>](http://msdn.microsoft.com/en-us/2947e1ad-8c44-4cdb-bbde-7683e186b41b)
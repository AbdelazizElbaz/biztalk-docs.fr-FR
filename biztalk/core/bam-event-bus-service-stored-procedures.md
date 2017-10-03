---
title: "Procédures stockées de Service Bus d’événements BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedures, Even Bus Service [BAM]
- Event Bus Service [BAM], stored procedures
ms.assetid: 18a7bd40-50ce-44f2-88ae-45a2e3c8d3f4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f44dce10113b8a3a85b7c1dd177f637933b582ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-event-bus-service-stored-procedures"></a><span data-ttu-id="29b68-102">Procédures stockées et service Bus d'événements BAM</span><span class="sxs-lookup"><span data-stu-id="29b68-102">BAM Event Bus Service Stored Procedures</span></span>
<span data-ttu-id="29b68-103">Utilisez les procédures stockées suivantes pour gérer le service Bus d'événements BAM :</span><span class="sxs-lookup"><span data-stu-id="29b68-103">You use the following stored procedures to manage the BAM Event Bus service:</span></span>  
  
-   <span data-ttu-id="29b68-104">Pour interrompre momentanément le service Bus d'événements BAM, exécutez la procédure stockée TDDS_BlockTDDS dans le cadre d'une transaction (sans valider la transaction) dans la base de données d'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="29b68-104">To pause the BAM Event Bus service, execute the TDDS_BlockTDDS stored procedure within a transaction (without committing the transaction) on the BAM database.</span></span> <span data-ttu-id="29b68-105">Pour relancer le service Bus d'événements BAM, validez la transaction TDDS_BlockTDDS.</span><span class="sxs-lookup"><span data-stu-id="29b68-105">To resume the BAM Event Bus service, commit the TDDS_BlockTDDS transaction.</span></span>  
  
-   <span data-ttu-id="29b68-106">Pour activer le service Bus d'événements BAM sur plusieurs ordinateurs, identifiez le ou les hôtes à utiliser pour le suivi et joignez ces ordinateurs à l'hôte de suivi.</span><span class="sxs-lookup"><span data-stu-id="29b68-106">To enable the BAM Event Bus service on multiple computers, identify which host(s) to use for tracking, and then join those computers to the tracking host.</span></span>  
  
-   <span data-ttu-id="29b68-107">Pour définir le délai d'attente de session et l'intervalle de pulsation, utilisez la procédure stockée TDDS_UpdateSettings.</span><span class="sxs-lookup"><span data-stu-id="29b68-107">To set up a session time-out and heartbeat interval, use the TDDS_UpdateSettings stored procedure.</span></span> <span data-ttu-id="29b68-108">Seuls les membres du groupe BTS_ADMIN_USERS ont l'autorisation d'exécuter cette procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="29b68-108">Only members of the BTS_ADMIN_USERS group have permission to execute this stored procedure.</span></span>  
  
     <span data-ttu-id="29b68-109">La procédure stockée TDDS_UpdateSettings peut être définie à l'aide des paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="29b68-109">The TDDS_UpdateSettings stored procedure has the following parameters:</span></span>  
  
    -   <span data-ttu-id="29b68-110">@RefreshIntervalint. doit être supérieur à 60 secondes.</span><span class="sxs-lookup"><span data-stu-id="29b68-110">@RefreshInterval int. Set to greater than 60 seconds.</span></span>  
  
    -   <span data-ttu-id="29b68-111">@SqlCommandTimeoutint. doit être inférieur à la valeur définie pour RefreshInterval.</span><span class="sxs-lookup"><span data-stu-id="29b68-111">@SqlCommandTimeout int. Set to less than RefreshInterval.</span></span>  
  
    -   <span data-ttu-id="29b68-112">@SessionTimeoutint. doit être deux fois supérieur à la valeur définie pour RefreshInterval.</span><span class="sxs-lookup"><span data-stu-id="29b68-112">@SessionTimeout int. Set to greater than two times the RefreshInterval.</span></span>  
  
    -   <span data-ttu-id="29b68-113">@EventLoggingIntervalnvarchar(16).</span><span class="sxs-lookup"><span data-stu-id="29b68-113">@EventLoggingInterval nvarchar(16).</span></span> <span data-ttu-id="29b68-114">doit être supérieur à 60 secondes.</span><span class="sxs-lookup"><span data-stu-id="29b68-114">Set to greater than 60 seconds.</span></span>  
  
    -   <span data-ttu-id="29b68-115">@RetryCountint. La valeur supérieure à 60 secondes</span><span class="sxs-lookup"><span data-stu-id="29b68-115">@RetryCount int. Set to greater than 60 seconds</span></span>  
  
    -   <span data-ttu-id="29b68-116">@ThreadPerSessionint. ce paramètre est obsolète.</span><span class="sxs-lookup"><span data-stu-id="29b68-116">@ThreadPerSession int. This parameter is obsolete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b68-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29b68-117">See Also</span></span>  
 [<span data-ttu-id="29b68-118">La gestion BAM</span><span class="sxs-lookup"><span data-stu-id="29b68-118">Managing BAM</span></span>](../core/managing-bam.md)
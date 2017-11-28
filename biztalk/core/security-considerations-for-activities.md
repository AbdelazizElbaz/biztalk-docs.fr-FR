---
title: "Considérations sur la sécurité pour les activités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fc49afd-a1c3-4ac7-8b89-11be667221e2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26ea453b24ac3e8df25e7a4da98f27731f3828be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-considerations-for-activities"></a><span data-ttu-id="67178-102">Considérations de sécurité pour les activités</span><span class="sxs-lookup"><span data-stu-id="67178-102">Security Considerations for Activities</span></span>
<span data-ttu-id="67178-103">Les rôles de sécurité utilisés lors de l'interception de l'adaptateur WCF sont les mêmes que ceux utilisés pour les autres solutions BAM.</span><span class="sxs-lookup"><span data-stu-id="67178-103">The security roles you use when intercepting the WCF adapter are the same as those used for other BAM solutions.</span></span> <span data-ttu-id="67178-104">Les considérations supplémentaires pour intercepter l'adaptateur WCF impliquent la sélection de l'utilisateur et du rôle d'écriture d'événement appropriés à utiliser.</span><span class="sxs-lookup"><span data-stu-id="67178-104">The additional considerations for intercepting the WCF adapter involve selecting the correct user and event writer role to use.</span></span>  
  
 <span data-ttu-id="67178-105">Lors de l'utilisation des services WCF et de l'adaptateur WCF, toutes les données BAM sont écrites dans la base de données Importation principale BAM par le rôle sélectionné.</span><span class="sxs-lookup"><span data-stu-id="67178-105">When using WCF services and the WCF adapter, all BAM-related data is written to the BAM Primary Import database by the selected role.</span></span>  
  
 <span data-ttu-id="67178-106">Vous pouvez sélectionner la configuration de rôle utilisateur appropriée en évaluant votre scénario de solution :</span><span class="sxs-lookup"><span data-stu-id="67178-106">You can select the proper user role configuration by assessing your solution scenario:</span></span>  
  
-   <span data-ttu-id="67178-107">Si votre solution nécessite de nombreux nouveaux services qui sont suivis par de nombreuses activités différentes, et qui sont tous exécutés sous le même compte utilisateur, il est avantageux d'utiliser le super rôle BAM_EVENT_WRITER pour écrire les événements interceptés.</span><span class="sxs-lookup"><span data-stu-id="67178-107">If your solution requires many new services that are tracked by many different activities, and are all run under the same user account, it is advantageous to use the BAM_EVENT_WRITER super role to write the intercepted events.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="67178-108">Les utilisateurs doivent être ajoutés au super rôle d'écriture d'événements BAM.</span><span class="sxs-lookup"><span data-stu-id="67178-108">Users must be added to the BAM event writer super role.</span></span> <span data-ttu-id="67178-109">Lors de l'ajout d'un utilisateur au super rôle il est important de se rappeler que l'utilisateur pourra alors écrire à toutes les activités dans le système.</span><span class="sxs-lookup"><span data-stu-id="67178-109">When adding a user to the super role it is important to remember that the user will then be able to write to all the activities in the system.</span></span>  
  
-   <span data-ttu-id="67178-110">Si votre solution nécessite un contrôle plus important des événements écrits, alors vous devez utiliser des rôles spécifiques à l'activité.</span><span class="sxs-lookup"><span data-stu-id="67178-110">If your solution requires greater control of the events written, then you should use activity-specific roles.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="67178-111">Les utilisateurs doivent être ajoutés au rôle d'écriture d'événements spécifique à l'activité.</span><span class="sxs-lookup"><span data-stu-id="67178-111">Users must be added to the activity specific event writer role for each activity.</span></span>  
  
 <span data-ttu-id="67178-112">Pour plus d’informations sur la configuration des rôles d’enregistreur d’événements BAM, consultez [comment déterminer et définir des rôles d’écriture d’événements pour les activités](../core/how-to-determine-and-set-event-writer-roles-for-activities.md).</span><span class="sxs-lookup"><span data-stu-id="67178-112">For more information about configuring the BAM event writer roles, see [How to Determine and Set Event Writer Roles for Activities](../core/how-to-determine-and-set-event-writer-roles-for-activities.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="67178-113">Vous devez être membre du groupe utilisateurs d’applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="67178-113">You must be a member of the BizTalk Application Users group.</span></span>  
  
 <span data-ttu-id="67178-114">Lors de la sélection du compte utilisateur à utiliser lors de la configuration de l'intercepteur WCF BAM pour la sécurité d'emprunt d'identité sous IIS vous devez prendre en compte les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="67178-114">When selecting the user account to use when configuring the BAM WCF interceptor for impersonation security under IIS you should consider the following scenarios:</span></span>  
  
-   <span data-ttu-id="67178-115">Auto-hébergé : Un exécutable en cours d’exécution sur votre ordinateur, qui contient le service WCF ouvert.</span><span class="sxs-lookup"><span data-stu-id="67178-115">Self-Hosted: An executable running on your computer that holds the WCF service open.</span></span>  
  
-   <span data-ttu-id="67178-116">Adaptateur WCF : Solutions créées à l’aide de la **Assistant Publication du Service WCF Biztalk**.</span><span class="sxs-lookup"><span data-stu-id="67178-116">WCF adapter: Solutions created using the **Biztalk WCF Service Publishing Wizard**.</span></span>  
  
-   <span data-ttu-id="67178-117">Hébergé par IIS : une solution hébergée dans une application IIS à l’aide d’un Service WCF.</span><span class="sxs-lookup"><span data-stu-id="67178-117">IIS hosted: A solution hosted in an IIS application using a WCF Service.</span></span>  
  
 <span data-ttu-id="67178-118">Utilisez le tableau suivant pour aider à identifier le compte à utiliser :</span><span class="sxs-lookup"><span data-stu-id="67178-118">Use the following table to help identify the account to use:</span></span>  
  
|<span data-ttu-id="67178-119">Type de solution</span><span class="sxs-lookup"><span data-stu-id="67178-119">Solution type</span></span>|<span data-ttu-id="67178-120">Compte à utiliser</span><span class="sxs-lookup"><span data-stu-id="67178-120">Account to use</span></span>|  
|-------------------|--------------------|  
|<span data-ttu-id="67178-121">Auto-hébergé</span><span class="sxs-lookup"><span data-stu-id="67178-121">Self-hosted</span></span>|<span data-ttu-id="67178-122">Le compte utilisé pour exécuter le fichier exécutable qui maintiendra le service ouvert.</span><span class="sxs-lookup"><span data-stu-id="67178-122">The account that is used to run the executable that will hold the service open.</span></span>|  
|<span data-ttu-id="67178-123">Adaptateur WCF</span><span class="sxs-lookup"><span data-stu-id="67178-123">WCF adapter</span></span>|<span data-ttu-id="67178-124">Utiliser l’identité du pool d’applications : il s’agit du pool d’applications associé au Vroot qui héberge l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="67178-124">Use the AppPool identity: This is the AppPool associated with the Vroot that houses the receive location.</span></span> <span data-ttu-id="67178-125">Cette identité est créée automatiquement lorsque vous utilisez la **Assistant Publication du Service WCF BizTalk** pour publier le site.</span><span class="sxs-lookup"><span data-stu-id="67178-125">This identity is created automatically when you use the **BizTalk WCF Service Publishing Wizard** to publish the site.</span></span> <span data-ttu-id="67178-126">Vous pouvez considérer ceci comme un cas spécial de solution hébergée IIS.</span><span class="sxs-lookup"><span data-stu-id="67178-126">You can consider this a special case of the IIS-hosted solution.</span></span>|  
|<span data-ttu-id="67178-127">Hébergé IIS</span><span class="sxs-lookup"><span data-stu-id="67178-127">IIS-hosted</span></span>|<span data-ttu-id="67178-128">L'identité de l'utilisateur AppPool exécutant le service WCF VRoot/Application.</span><span class="sxs-lookup"><span data-stu-id="67178-128">The identity of the AppPool user running the WCF service VRoot/Application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67178-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67178-129">See Also</span></span>  
 [<span data-ttu-id="67178-130">Considérations de sécurité pour les intercepteurs BAM</span><span class="sxs-lookup"><span data-stu-id="67178-130">Security Considerations for BAM Interceptors</span></span>](../core/security-considerations-for-bam-interceptors.md)
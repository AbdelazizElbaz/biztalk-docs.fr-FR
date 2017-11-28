---
title: "Comment configurer des filtres pour un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters, configuring
- filters, send ports
- configuring, filters
- managing [send ports], configuring
- send ports, configuring
- send ports, filters
- managing [send ports], filters
ms.assetid: ad13ca8e-bb1d-4449-8163-49dd9d5d92f8
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7845b6189f86054ba9661ea450575a2dcfe47953
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-filters-for-a-send-port"></a><span data-ttu-id="839da-102">Configuration des filtres pour un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="839da-102">How to Configure Filters for a Send Port</span></span>
<span data-ttu-id="839da-103">Cette rubrique décrit la configuration des filtres pour un port d'envoi à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="839da-103">This topic describes how to use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to configure filters for a send port.</span></span> <span data-ttu-id="839da-104">Les filtres vous permettent de créer des applications de routage basé sur le contenu ou de messagerie simple.</span><span class="sxs-lookup"><span data-stu-id="839da-104">You can use filters to create simple messaging or content-based routing (CBR) applications.</span></span> <span data-ttu-id="839da-105">Un filtre définit des conditions pour les champs ou les propriétés de message qui déterminent les messages acheminés au port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="839da-105">A filter sets conditions for message properties or fields that determine which messages are routed to the send port.</span></span> <span data-ttu-id="839da-106">Un filtre ne filtre pas les messages qu'une orchestration achemine vers le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="839da-106">A filter does not filter the messages that an orchestration routes to the send port.</span></span>  
  
 <span data-ttu-id="839da-107">Vous pouvez créer une ou plusieurs expressions de filtre, lesquelles sont constituées d'une propriété de message, d'un opérateur et d'une valeur validée avec la propriété par le biais de l'opérateur.</span><span class="sxs-lookup"><span data-stu-id="839da-107">You can create one or more filter expressions, which consist of a message property, an operator, and a value that is validated against the property by using the operator.</span></span>  
  
 <span data-ttu-id="839da-108">Par exemple, vous pouvez créer l'expression suivante :</span><span class="sxs-lookup"><span data-stu-id="839da-108">For example, you might create an expression like the following:</span></span>  
  
 <span data-ttu-id="839da-109">MSMQ.MsgID = 1</span><span class="sxs-lookup"><span data-stu-id="839da-109">MSMQ.MsgID = 1</span></span>  
  
 <span data-ttu-id="839da-110">Avec ce filtre, le groupe de ports d'envoi s'abonnera uniquement aux messages ayant un ID de message MSMQ correspondant à 1.</span><span class="sxs-lookup"><span data-stu-id="839da-110">With this filter, the send port group would only subscribe to messages having an MSMQ message ID of 1.</span></span>  
  
 <span data-ttu-id="839da-111">Vous pouvez créer des expressions supplémentaires et leur définir une relation AND ou OR avec d'autres expressions, par exemple :</span><span class="sxs-lookup"><span data-stu-id="839da-111">You can create additional expressions and specify that they have an AND or OR relationship with other expressions, for example:</span></span>  
  
 <span data-ttu-id="839da-112">MSMQ.MsgID = 1 OR</span><span class="sxs-lookup"><span data-stu-id="839da-112">MSMQ.MsgID = 1 OR</span></span>  
  
 <span data-ttu-id="839da-113">SMTP.From = MyServer</span><span class="sxs-lookup"><span data-stu-id="839da-113">SMTP.From = MyServer</span></span>  
  
 <span data-ttu-id="839da-114">Dans ce cas, le groupe de ports d'envoi s'abonnera à tous les messages ayant un ID de message MSMQ de 1 ou qui proviennent du serveur SMTP nommé MyServer.</span><span class="sxs-lookup"><span data-stu-id="839da-114">In this case, the send port group would subscribe to all messages that have either an MSMQ message ID of 1 or that have been sent from the SMTP server named MyServer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="839da-115">Si vous créez un filtre pour un port d'envoi dans une application qui utilise un schéma de propriété d'une autre application et que vous importiez ensuite la première application dans un nouveau groupe BizTalk, vous ne recevrez pas de message vous avertissant de l'absence de schéma et le filtrage ne fonctionnera pas une fois l'application installée et démarrée.</span><span class="sxs-lookup"><span data-stu-id="839da-115">If you create a filter for a send port in one application that uses a property schema in another application, and then import the first application into a new BizTalk group, you will not receive a warning that the schema is missing, and filtering will not function when the application is installed and started.</span></span> <span data-ttu-id="839da-116">Vous pouvez corriger ce problème en important l'application qui contient le schéma avant d'installer l'application sans schéma.</span><span class="sxs-lookup"><span data-stu-id="839da-116">You can correct the problem by importing the application that contains the schema before you install the application that does not contain the schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="839da-117">Le développeur peut configurer des filtres pour un port d'envoi au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="839da-117">The application developer can configure filters for a send port during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="839da-118">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="839da-118">Prerequisites</span></span>  
 <span data-ttu-id="839da-119">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe des administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="839da-119">To perform the procedure in this topic, you must be logged on with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span> <span data-ttu-id="839da-120">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="839da-120">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-configure-filters-for-a-send-port"></a><span data-ttu-id="839da-121">Pour configurer les filtres d'un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="839da-121">To configure filters for a send port</span></span>  
  
1.  <span data-ttu-id="839da-122">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="839da-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="839da-123">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk pour laquelle configurer des filtres de port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="839da-123">In the console tree, expand the BizTalk group and the BizTalk application for which you want to configure send port filters.</span></span>  
  
3.  <span data-ttu-id="839da-124">Développez **Ports d’envoi**, cliquez sur le port d’envoi, cliquez sur **propriétés**, puis cliquez sur **filtres**.</span><span class="sxs-lookup"><span data-stu-id="839da-124">Expand **Send Ports**, right-click the send port, click **Properties**, and then click **Filters**.</span></span>  
  
4.  <span data-ttu-id="839da-125">Configurer des filtres comme décrit dans le tableau suivant, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="839da-125">Configure filters as described in the following table, and then click **OK**.</span></span>  
  
    |<span data-ttu-id="839da-126">Utiliser</span><span class="sxs-lookup"><span data-stu-id="839da-126">Use this</span></span>|<span data-ttu-id="839da-127">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="839da-127">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="839da-128">**Delete**</span><span class="sxs-lookup"><span data-stu-id="839da-128">**Delete**</span></span>|<span data-ttu-id="839da-129">Supprimer l'expression de filtre sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="839da-129">Click to delete the selected filter expression.</span></span>|  
    |<span data-ttu-id="839da-130">**Monter**</span><span class="sxs-lookup"><span data-stu-id="839da-130">**Move Up**</span></span>|<span data-ttu-id="839da-131">Déplacer la propriété sélectionnée vers le haut de la séquence d'expression du filtre.</span><span class="sxs-lookup"><span data-stu-id="839da-131">Click to move the selected property ahead in the filter expression sequence.</span></span>|  
    |<span data-ttu-id="839da-132">**Descendre**</span><span class="sxs-lookup"><span data-stu-id="839da-132">**Move Down**</span></span>|<span data-ttu-id="839da-133">Déplacer la propriété sélectionnée vers le bas de la séquence d'expression du filtre.</span><span class="sxs-lookup"><span data-stu-id="839da-133">Click to move the selected property down in the filter expression sequence.</span></span>|  
    |<span data-ttu-id="839da-134">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="839da-134">**Property**</span></span>|<span data-ttu-id="839da-135">Dans la liste, cliquer sur une propriété de message à utiliser dans cette expression de filtre.</span><span class="sxs-lookup"><span data-stu-id="839da-135">In the list, click a message property to use in this filter expression.</span></span>|  
    |<span data-ttu-id="839da-136">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="839da-136">**Operator**</span></span>|<span data-ttu-id="839da-137">Entrer ou sélectionner l'opérateur de l'expression.</span><span class="sxs-lookup"><span data-stu-id="839da-137">Type or select the operator for the expression.</span></span>|  
    |<span data-ttu-id="839da-138">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="839da-138">**Value**</span></span>|<span data-ttu-id="839da-139">Taper la valeur à valider pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="839da-139">Type the value to validate against the property.</span></span> <span data-ttu-id="839da-140">Le type de valeur accepté varie en fonction du type de propriété.</span><span class="sxs-lookup"><span data-stu-id="839da-140">The accepted value type varies according to the type of property.</span></span> <span data-ttu-id="839da-141">Pour afficher le type de valeur autorisé pour une propriété, placez votre souris sur la propriété.</span><span class="sxs-lookup"><span data-stu-id="839da-141">To see what type of value is accepted for a property, hover your mouse over the property.</span></span> <span data-ttu-id="839da-142">Les valeurs acceptables sont les suivants : Int : (entier) il doit être un nombre entier.</span><span class="sxs-lookup"><span data-stu-id="839da-142">Acceptable values are as follows: Int: (Integer) This must be a whole number.</span></span> <span data-ttu-id="839da-143">Chaîne : Une chaîne de caractères.</span><span class="sxs-lookup"><span data-stu-id="839da-143">String: A character string.</span></span> <span data-ttu-id="839da-144">dateTime : une date et/ou une heure dans. NET-format pris en charge.</span><span class="sxs-lookup"><span data-stu-id="839da-144">dateTime: A date and/or time in .NET-supported format.</span></span> <span data-ttu-id="839da-145">Pour plus d'informations sur les formats d'heure pris en charge par .NET, voir la rubrique « DateTimeFormatInfo Class » de l'aide .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="839da-145">For more information about .NET-supported time formats, see "DateTimeFormatInfo Class" in .NET Frameworks Help.</span></span>|  
    |<span data-ttu-id="839da-146">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="839da-146">**Group by**</span></span>|<span data-ttu-id="839da-147">Sélectionnez **et** ou **ou** pour indiquer la relation entre ceci et autres expressions de filtre.</span><span class="sxs-lookup"><span data-stu-id="839da-147">Select **And** or **Or** to indicate the relationship between this and other filter expressions.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="839da-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="839da-148">See Also</span></span>  
 [<span data-ttu-id="839da-149">Création et configuration des Ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="839da-149">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)
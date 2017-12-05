---
title: "Files d’attente de file d’attente de messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [MSMQ adapters], queue paths
- naming conventions, MSMQ adapters
- configuring [MSMQ adapters], naming conventions
- messages, queuing
- MSMQ adapters, troubleshooting
- MSMQ adapters, message queues
- configuring [MSMQ adapters], troubleshooting
- troubleshooting, queue paths [MSMQ adapters]
- naming conventions, queue paths [MSMQ adapters]
- configuring [MSMQ adapters], message queues
ms.assetid: b802348e-8543-4b06-a6e4-149b86139fb1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa8d2521a8cf434c7a0ea56f749f9df3f032551e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="message-queuing-queues"></a><span data-ttu-id="069d1-102">Files d’attente de file d’attente</span><span class="sxs-lookup"><span data-stu-id="069d1-102">Message Queuing Queues</span></span>
<span data-ttu-id="069d1-103">Cette section décrit la spécification de files d'attentes Microsoft Message Queuing (également appelé MSMQ) lors de l'utilisation de l'adaptateur MSMQ.</span><span class="sxs-lookup"><span data-stu-id="069d1-103">This section describes how to specify Microsoft Message Queuing (also known as MSMQ) queues when you use the MSMQ adapter.</span></span> <span data-ttu-id="069d1-104">Elle décrit les conventions utilisées lors de la spécification de chemins d'accès ainsi que le rôle joué par les noms de formats dans la conversion de chemins en désignations de file d'attente.</span><span class="sxs-lookup"><span data-stu-id="069d1-104">It describes the conventions for specifying paths and also describes the role that format names play in translating paths into queue designations.</span></span>  
  
## <a name="queue-path-naming-conventions"></a><span data-ttu-id="069d1-105">Conventions d'affectation de noms aux chemins des files d'attente</span><span class="sxs-lookup"><span data-stu-id="069d1-105">Queue Path Naming Conventions</span></span>  
 <span data-ttu-id="069d1-106">Lorsque le nom de la file d'attente fait référence à un chemin, utilisez les conventions d'affectation de noms décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="069d1-106">If the queue name refers to a path, use the naming conventions in the following table.</span></span>  
  
|<span data-ttu-id="069d1-107">**Type de file d'attente**</span><span class="sxs-lookup"><span data-stu-id="069d1-107">**Queue type**</span></span>|<span data-ttu-id="069d1-108">**Syntaxe de chemin d’accès**</span><span class="sxs-lookup"><span data-stu-id="069d1-108">**Syntax for path**</span></span>|  
|--------------------|-------------------------|  
|<span data-ttu-id="069d1-109">File d'attente publique</span><span class="sxs-lookup"><span data-stu-id="069d1-109">Public queue</span></span>|<span data-ttu-id="069d1-110">*Nom_Ordinateur*\QueueName</span><span class="sxs-lookup"><span data-stu-id="069d1-110">*Computername*\QueueName</span></span>|  
|<span data-ttu-id="069d1-111">File d'attente privée</span><span class="sxs-lookup"><span data-stu-id="069d1-111">Private queue</span></span>|<span data-ttu-id="069d1-112">*Nom_Ordinateur*\Private$\QueueName</span><span class="sxs-lookup"><span data-stu-id="069d1-112">*Computername*\Private$\QueueName</span></span>|  
|<span data-ttu-id="069d1-113">File d'attente du journal</span><span class="sxs-lookup"><span data-stu-id="069d1-113">Journal queue</span></span>|<span data-ttu-id="069d1-114">*Nom_Ordinateur*\QueueName\Journal$</span><span class="sxs-lookup"><span data-stu-id="069d1-114">*Computername*\QueueName\Journal$</span></span>|  
|<span data-ttu-id="069d1-115">File d’attente du journal de l’ordinateur **Remarque :** utilisation de la file d’attente de réception uniquement.</span><span class="sxs-lookup"><span data-stu-id="069d1-115">Computer journal queue **Note:**  Use for receive queue only.</span></span>|<span data-ttu-id="069d1-116">*Nom_Ordinateur*\Journal$</span><span class="sxs-lookup"><span data-stu-id="069d1-116">*Computername*\Journal$</span></span>|  
|<span data-ttu-id="069d1-117">File d’attente de lettres mortes ordinateur **Remarque :** utilisation de la file d’attente de réception uniquement.</span><span class="sxs-lookup"><span data-stu-id="069d1-117">Computer dead-letter queue **Note:**  Use for receive queue only.</span></span>|<span data-ttu-id="069d1-118">*Nom_Ordinateur*\Deadletter$</span><span class="sxs-lookup"><span data-stu-id="069d1-118">*Computername*\Deadletter$</span></span>|  
|<span data-ttu-id="069d1-119">File d’attente de lettres mortes de transaction ordinateur **Remarque :** utilisation de la file d’attente de réception uniquement.</span><span class="sxs-lookup"><span data-stu-id="069d1-119">Computer transaction dead-letter queue **Note:**  Use for receive queue only.</span></span>|<span data-ttu-id="069d1-120">*Nom_Ordinateur*\XactDeadletter$</span><span class="sxs-lookup"><span data-stu-id="069d1-120">*Computername*\XactDeadletter$</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="069d1-121">Le chemin de la file d'attente doit être unique.</span><span class="sxs-lookup"><span data-stu-id="069d1-121">The path of the queue must be unique.</span></span>  
  
 <span data-ttu-id="069d1-122">Lorsque le nom de la file d'attente fait référence à un nom de format, il prend la forme d'une chaîne qui indique si la file d'attente est publique ou privée, suivie par un GUID généré pour la file d'attente ainsi que par d'autres identificateurs, selon le besoin.</span><span class="sxs-lookup"><span data-stu-id="069d1-122">If the queue name refers to a format name, it takes the form of a string that indicates whether a queue is public or private, followed by a generated GUID for the queue and other identifiers as needed.</span></span> <span data-ttu-id="069d1-123">Utilisez les conventions d'affectation de noms décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="069d1-123">Use the naming conventions in the following table.</span></span>  
  
|<span data-ttu-id="069d1-124">**Type de format**</span><span class="sxs-lookup"><span data-stu-id="069d1-124">**Format type**</span></span>|<span data-ttu-id="069d1-125">**Syntaxe de nom de format**</span><span class="sxs-lookup"><span data-stu-id="069d1-125">**Syntax for format name**</span></span>|  
|---------------------|--------------------------------|  
|<span data-ttu-id="069d1-126">Public</span><span class="sxs-lookup"><span data-stu-id="069d1-126">Public</span></span>|<span data-ttu-id="069d1-127">*FormatName*: Public = Guidfileattente</span><span class="sxs-lookup"><span data-stu-id="069d1-127">*FormatName*:Public=QueueGUID</span></span>|  
|<span data-ttu-id="069d1-128">Direct</span><span class="sxs-lookup"><span data-stu-id="069d1-128">Direct</span></span>|<span data-ttu-id="069d1-129">*FormatName*: DIRECT = SPX:NetworkNumber:HostNumber\QueueName</span><span class="sxs-lookup"><span data-stu-id="069d1-129">*FormatName*:DIRECT=SPX:NetworkNumber:HostNumber\QueueName</span></span><br /><br /> <span data-ttu-id="069d1-130">*FormatName*: DIRECT = TCP : adresseip\nomfileattente</span><span class="sxs-lookup"><span data-stu-id="069d1-130">*FormatName*: DIRECT=TCP:IPAddress\QueueName</span></span><br /><br /> <span data-ttu-id="069d1-131">*FormatName*: DIRECT = OS : NomOrdinateur\NomFileAttente</span><span class="sxs-lookup"><span data-stu-id="069d1-131">*FormatName*: DIRECT=OS:ComputerName\QueueName</span></span>|  
  
 <span data-ttu-id="069d1-132">Si le chemin de la file d'attente du port d'envoi est une liste de distribution, sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="069d1-132">If the send port queue path is a distribution list, then the queue path syntax is:</span></span>  
  
 <span data-ttu-id="069d1-133">DL=GUIDListeDistribution</span><span class="sxs-lookup"><span data-stu-id="069d1-133">DL=DistributionListGUID</span></span>  
  
 <span data-ttu-id="069d1-134">Si le chemin de la file d'attente d'envoi ou de réception est une URL HTTP ou HTTPS, la syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="069d1-134">If the send or receive queue path is an HTTP or HTTPS URL, then the syntax is:</span></span>  
  
 <span data-ttu-id="069d1-135">NomFormat : direct = http : / /\<nom de client\>/msmq/\<nom de la file d’attente\></span><span class="sxs-lookup"><span data-stu-id="069d1-135">FormatName:DIRECT=http://\<client name\>/msmq/\<queue name\></span></span>  
  
 <span data-ttu-id="069d1-136">NomFormat : direct = https : / /\<nom de client\>/msmq/\<nom de la file d’attente\></span><span class="sxs-lookup"><span data-stu-id="069d1-136">FormatName:DIRECT=https://\<client name\>/msmq/\<queue name\></span></span>  
  
> [!NOTE]
>  <span data-ttu-id="069d1-137">« msmq » correspond au répertoire virtuel créé par Message Queuing dans IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="069d1-137">"msmq" is the virtual folder that Message Queuing creates in Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="069d1-138">Vous pouvez uniquement utiliser le protocole HTTP pour envoyer des messages.</span><span class="sxs-lookup"><span data-stu-id="069d1-138">You can only use HTTP to send messages.</span></span> <span data-ttu-id="069d1-139">Il est impossible de lire des messages dans une file d'attente située sur un ordinateur distant si celle-ci est ouverte à l'aide d'un nom de format direct HTTP.</span><span class="sxs-lookup"><span data-stu-id="069d1-139">You cannot read messages in a queue on a remote computer if the queue is opened using an HTTP direct format name.</span></span> <span data-ttu-id="069d1-140">Toutefois, vous pouvez toujours recevoir des messages SOAP (formatés) à partir d'une file d'attente distante à l'aide du chemin de la file d'attente publique ou privée sans le protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="069d1-140">However, you can still receive SOAP (formatted) messages from a remote queue by using the private or public queue path without HTTP.</span></span>  
  
 <span data-ttu-id="069d1-141">Si le nom de la file d'attente fait référence à un nom constitué de texte descriptif que l'administrateur a spécifié pour cette file d'attente, la syntaxe du chemin de file d'attente faisant référence à ce nom est la suivante :</span><span class="sxs-lookup"><span data-stu-id="069d1-141">If the queue name refers to a descriptive text label that the administrator specified for the queue, then the syntax of the queue path referring to this label is:</span></span>  
  
 <span data-ttu-id="069d1-142">LABEL:MyQueue</span><span class="sxs-lookup"><span data-stu-id="069d1-142">LABEL:MyQueue</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="069d1-143">Les noms ne sont pas toujours uniques.</span><span class="sxs-lookup"><span data-stu-id="069d1-143">Labels are not always unique.</span></span> <span data-ttu-id="069d1-144">Toutefois, vous recevrez une erreur s'il existe un conflit de noms lorsque vous tentez de vous connecter à une file d'attente spécifique à l'aide de son nom.</span><span class="sxs-lookup"><span data-stu-id="069d1-144">Therefore, you will receive an error if a name conflict exists when you try to connect to a specific queue by using its label.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="069d1-145">Le nom est un paramètre de champ de transport obligatoire pour l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="069d1-145">The label is a required transport field for the adapter.</span></span>  
  
## <a name="role-of-the-format-name"></a><span data-ttu-id="069d1-146">Rôle du nom de format</span><span class="sxs-lookup"><span data-stu-id="069d1-146">Role of the Format Name</span></span>  
 <span data-ttu-id="069d1-147">Le nom de format permet à Message Queuing d'identifier une file d'attente et de déterminer la manière d'y accéder.</span><span class="sxs-lookup"><span data-stu-id="069d1-147">Message Queuing uses the format name to identify a queue and to determine how to access it.</span></span> <span data-ttu-id="069d1-148">Message Queuing attribue le nom de format à la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="069d1-148">Message Queuing assigns the format name to the queue.</span></span>  
  
 <span data-ttu-id="069d1-149">Lorsque vous spécifiez une file d'attente à l'aide de la syntaxe du nom de chemin, par exemple myMachine\myQueue, Message Queuing recherche le chemin pour identifier le nom de format qui lui est associé.</span><span class="sxs-lookup"><span data-stu-id="069d1-149">When you specify a queue using the path name syntax, for example myMachine\myQueue, Message Queuing looks up the path to find the associated format name.</span></span> <span data-ttu-id="069d1-150">Message Queuing utilise ensuite ce nom de format pour accéder à la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="069d1-150">Message Queuing then uses that format name to access the queue.</span></span> <span data-ttu-id="069d1-151">Lorsque vous spécifiez le nom de format, Message Queuing utilise celui que vous indiquez.</span><span class="sxs-lookup"><span data-stu-id="069d1-151">When you specify the format name, Message Queuing uses the format name you use.</span></span>  
  
 <span data-ttu-id="069d1-152">Pour plus d'informations sur les noms de formats, consultez la rubrique « Propriété MessageQueue.FormatName » dans l'aide de la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="069d1-152">For more information about format names, see "MessageQueue.FormatName Property" in .NET Framework Class Library Help.</span></span>  
  
## <a name="troubleshooting-queue-paths"></a><span data-ttu-id="069d1-153">Résolution des problèmes relatifs aux chemins des files d'attente</span><span class="sxs-lookup"><span data-stu-id="069d1-153">Troubleshooting Queue Paths</span></span>  
  
-   <span data-ttu-id="069d1-154">Une exception se produit si la syntaxe du chemin de file d'attente renseigné ne correspond à aucun des formats décrits précédemment dans la partie « Conventions d'affectation de noms aux chemins des files d'attente ».</span><span class="sxs-lookup"><span data-stu-id="069d1-154">An exception occurs if the syntax of the provided queue path does not match one of the formats described earlier in "Queue Path Naming Conventions."</span></span>  
  
-   <span data-ttu-id="069d1-155">Les caractères suivants sont non valides pour la spécification du nom de l'ordinateur dans le chemin de file d'attente :</span><span class="sxs-lookup"><span data-stu-id="069d1-155">The following are not valid characters for computer names in the queue path:</span></span>  
  
     <span data-ttu-id="069d1-156">\ ; , + "</span><span class="sxs-lookup"><span data-stu-id="069d1-156">\ ; , + "</span></span>  
  
     <span data-ttu-id="069d1-157">Une exception se produit si le nom d'un ordinateur est un nombre.</span><span class="sxs-lookup"><span data-stu-id="069d1-157">An exception occurs if the computer name is a number.</span></span> <span data-ttu-id="069d1-158">Par exemple : 234\private$ \queue.</span><span class="sxs-lookup"><span data-stu-id="069d1-158">For example: 234\private$\queue.</span></span>  
  
-   <span data-ttu-id="069d1-159">Pour la file d'attente des messages non distribués de l'ordinateur, la file d'attente du journal de l'ordinateur et pour la file d'attente des messages non distribués des transactions de l'ordinateur, une exception se produit lorsqu'un utilisateur spécifie l'une des files d'attente du système comme file d'attente de destination pour l'envoi.</span><span class="sxs-lookup"><span data-stu-id="069d1-159">For a computer dead-letter queue, computer journal queue, and computer transaction dead-letter queue, an exception occurs if the user specifies any one of the system queues as the destination queue for send.</span></span>  
  
-   <span data-ttu-id="069d1-160">**System.Messaging.MessageQueue.Exists** ne fonctionne pas pour les files d’attente distantes.</span><span class="sxs-lookup"><span data-stu-id="069d1-160">**System.Messaging.MessageQueue.Exists** does not work for remote queues.</span></span> <span data-ttu-id="069d1-161">Pour plus d'informations, consultez la rubrique « Méthode MessageQueue.Exists » dans l'aide de la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="069d1-161">For more information, see "MessageQueue.Exists Method" in .NET Framework Class Library Help.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="069d1-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="069d1-162">See Also</span></span>  
 [<span data-ttu-id="069d1-163">Configuration de l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="069d1-163">Configuring the MSMQ Adapter</span></span>](../core/configuring-the-msmq-adapter.md)
---
title: "Le modèle de Message d’InfoPath | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bb055b1-8480-44dd-8739-f2981bca63c3
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b8ec04d16da25f39060540aa8a8205421397d18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-infopath-message-template"></a><span data-ttu-id="4f699-102">Le modèle de Message d’InfoPath</span><span class="sxs-lookup"><span data-stu-id="4f699-102">The InfoPath Message Template</span></span>
<span data-ttu-id="4f699-103">Comme alternative à l’affichage de messages d’erreur ESB dans le portail de gestion ESB, les utilisateurs peuvent tirer parti d’un modèle de message Microsoft InfoPath nommé l’Afficheur des messages d’Exception ESB, fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4f699-103">As an alternative to viewing ESB fault messages in the ESB Management Portal, users can take advantage of a Microsoft InfoPath message template named the ESB Exception Message Viewer, provided with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span>  
  
 <span data-ttu-id="4f699-104">L’infrastructure de gestion d’Exception ESB peut conserver les messages dans un format sérialisé affichant, ainsi que le modèle ESB Exception l’Afficheur des messages, plusieurs vues de message d’erreur et les messages d’origine qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="4f699-104">The ESB Exception Management Framework can persist messages in a serialized format that, together with the ESB Exception Message Viewer template, will display several views of the fault message and the original messages it contains.</span></span> <span data-ttu-id="4f699-105">L’Afficheur des messages d’Exception ESB propose les vues suivantes :</span><span class="sxs-lookup"><span data-stu-id="4f699-105">The ESB Exception Message Viewer provides the following views:</span></span>  
  
-   <span data-ttu-id="4f699-106">vue Général ;</span><span class="sxs-lookup"><span data-stu-id="4f699-106">General view</span></span>  
  
-   <span data-ttu-id="4f699-107">Vue de l’objet exception</span><span class="sxs-lookup"><span data-stu-id="4f699-107">Exception Object view</span></span>  
  
-   <span data-ttu-id="4f699-108">vue Messages</span><span class="sxs-lookup"><span data-stu-id="4f699-108">Messages view</span></span>  
  
 <span data-ttu-id="4f699-109">La figure 1 illustre la vue générale de l’Afficheur des messages d’Exception ESB, qui affiche plus les propriétés ambiantes de l’exception.</span><span class="sxs-lookup"><span data-stu-id="4f699-109">Figure 1 shows the General view of the ESB Exception Message Viewer, which displays most ambient properties of the exception.</span></span>  
  
 <span data-ttu-id="4f699-110">![Vue générale du Message d’exception](../esb-toolkit/media/ch4-exceptionmessagegeneralview.gif "ExceptionMessageGeneralView de chapitre 4")</span><span class="sxs-lookup"><span data-stu-id="4f699-110">![Exception Message General View](../esb-toolkit/media/ch4-exceptionmessagegeneralview.gif "Ch4-ExceptionMessageGeneralView")</span></span>  
  
 <span data-ttu-id="4f699-111">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="4f699-111">**Figure 1**</span></span>  
  
 <span data-ttu-id="4f699-112">**L’Afficheur des messages d’Exception ESB affichant la vue générale**</span><span class="sxs-lookup"><span data-stu-id="4f699-112">**The ESB Exception Message Viewer showing the General view**</span></span>  
  
 <span data-ttu-id="4f699-113">La figure 2 illustre la vue de l’objet d’Exception, qui affiche les propriétés et la trace de pile à partir de la **System.Exception** objet.</span><span class="sxs-lookup"><span data-stu-id="4f699-113">Figure 2 shows the Exception Object view, which displays the properties and the stack trace from the **System.Exception** object.</span></span>  
  
 <span data-ttu-id="4f699-114">![Objet d’Exception exception Message](../esb-toolkit/media/ch4-exceptionmessageexceptionobject.gif "ExceptionMessageExceptionObject de chapitre 4")</span><span class="sxs-lookup"><span data-stu-id="4f699-114">![Exception Message Exception Object](../esb-toolkit/media/ch4-exceptionmessageexceptionobject.gif "Ch4-ExceptionMessageExceptionObject")</span></span>  
  
 <span data-ttu-id="4f699-115">**Figure 2**</span><span class="sxs-lookup"><span data-stu-id="4f699-115">**Figure 2**</span></span>  
  
 <span data-ttu-id="4f699-116">**L’Afficheur des messages d’Exception ESB affichant la vue de l’objet Exception**</span><span class="sxs-lookup"><span data-stu-id="4f699-116">**The ESB Exception Message Viewer showing the Exception Object view**</span></span>  
  
 <span data-ttu-id="4f699-117">Figure 3 illustre l’affichage de Messages, qui fournit une liste déroulante à partir de laquelle l’utilisateur peut sélectionner à partir des messages persistants disponibles.</span><span class="sxs-lookup"><span data-stu-id="4f699-117">Figure 3 shows the Messages view, which provides a drop-down list from which the user can select from available persisted messages.</span></span> <span data-ttu-id="4f699-118">La vue affiche les valeurs des propriétés de contexte du message persistant et le contenu du message XML.</span><span class="sxs-lookup"><span data-stu-id="4f699-118">The view displays the values of the context properties of the persisted message and the XML message content.</span></span>  
  
 <span data-ttu-id="4f699-119">![Affichage des Messages de Message d’exception](../esb-toolkit/media/ch4-exceptionmessagemessagesview.gif "ExceptionMessageMessagesView de chapitre 4")</span><span class="sxs-lookup"><span data-stu-id="4f699-119">![Exception Message Messages View](../esb-toolkit/media/ch4-exceptionmessagemessagesview.gif "Ch4-ExceptionMessageMessagesView")</span></span>  
  
 <span data-ttu-id="4f699-120">**Figure 3**</span><span class="sxs-lookup"><span data-stu-id="4f699-120">**Figure 3**</span></span>  
  
 <span data-ttu-id="4f699-121">**L’Afficheur des messages d’Exception ESB affichant la vue Messages**</span><span class="sxs-lookup"><span data-stu-id="4f699-121">**The ESB Exception Message Viewer showing the Messages view**</span></span>
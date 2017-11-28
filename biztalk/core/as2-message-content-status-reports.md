---
title: "AS2 Rapports d’état du contenu du Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6244aa59-a80d-450b-ab95-9a5e14c0c40e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b2dadb3231136255dcf532e5054c1a6228880f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-message-content-status-reports"></a><span data-ttu-id="4b138-102">Rapports d'état sur le contenu d'un message AS2</span><span class="sxs-lookup"><span data-stu-id="4b138-102">AS2 Message Content Status Reports</span></span>

## <a name="overview"></a><span data-ttu-id="4b138-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="4b138-103">Overview</span></span>
<span data-ttu-id="4b138-104">Les rapports d'état suivants affichent les propriétés de contexte, les en-têtes et la charge d'un message AS2 ou d'un MDN.</span><span class="sxs-lookup"><span data-stu-id="4b138-104">These status reports display the context properties, headers and payload of an AS2 message or an MDN.</span></span> <span data-ttu-id="4b138-105">Trois rapports d'état sur le contenu d'un message AS2 existent :</span><span class="sxs-lookup"><span data-stu-id="4b138-105">There are three AS2 message content status reports:</span></span>  
  
-   <span data-ttu-id="4b138-106">rapport de message au format câble ;</span><span class="sxs-lookup"><span data-stu-id="4b138-106">Message Wire Format report</span></span>  
  
-   <span data-ttu-id="4b138-107">rapport de message au format décodé ;</span><span class="sxs-lookup"><span data-stu-id="4b138-107">Message Decoded Format report</span></span>  
  
-   <span data-ttu-id="4b138-108">rapport de message MDN.</span><span class="sxs-lookup"><span data-stu-id="4b138-108">Mdn Message report</span></span>  
  
 <span data-ttu-id="4b138-109">Afficher l’un de ces rapports en double-cliquant sur un message AS2 dans le rapport d’état AS2/MDN, puis en cliquant **vue Message au Format câble**, **vue Message au Format décodé**, ou **vue Mdn Message**.</span><span class="sxs-lookup"><span data-stu-id="4b138-109">You display one of these reports by right-clicking an AS2 message within the AS2/MDN status report, and then clicking **View Message Wire Format**, **View Message Decoded Format**, or **View Mdn Message**.</span></span> <span data-ttu-id="4b138-110">La commande MDN affiche le MDN corrélé au message AS2.</span><span class="sxs-lookup"><span data-stu-id="4b138-110">The MDN command will display the MDN that is correlated to the AS2 message.</span></span>  
  
 <span data-ttu-id="4b138-111">Ces rapports ne sont disponibles que si vous avez sélectionné les propriétés « Stocker les messages dans une base de données de non-répudiation » correspondantes sur la page Tiers considéré comme expéditeur des messages AS2 ou la page Tiers considéré comme récepteur des messages AS2 de la boîte de dialogue Propriétés AS2 relative au tiers associé.</span><span class="sxs-lookup"><span data-stu-id="4b138-111">Each of these reports is available only if you have selected the corresponding "Store messages in non-repudiation database" properties in the Party as AS2 Message Sender page or Party as AS2 Message Receiver page of the AS2 Properties dialog box for the related party.</span></span> <span data-ttu-id="4b138-112">La commande stocke les messages AS2 ou les MDN au format câble ou décodé dans la base de données BizTalkDTADb.</span><span class="sxs-lookup"><span data-stu-id="4b138-112">The commands store AS2 messages or MDNs in wire format or decoded format in the BizTalkDTADb database.</span></span>  
  
 <span data-ttu-id="4b138-113">Ce rapport utilise la **boîte de dialogue Propriétés de Message détails** (consultez les détails de l’interface utilisateur [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]) pour afficher les données du message, avec les informations séparées en pages :</span><span class="sxs-lookup"><span data-stu-id="4b138-113">This report uses the **Message Details Properties Dialog Box** (see the UI details [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]) to display message data, with information separated into pages:</span></span>  
  
|<span data-ttu-id="4b138-114">Radiomessagerie</span><span class="sxs-lookup"><span data-stu-id="4b138-114">Page</span></span>|<span data-ttu-id="4b138-115">Données affichées</span><span class="sxs-lookup"><span data-stu-id="4b138-115">Data Displayed</span></span>|  
|----------|--------------------|  
|<span data-ttu-id="4b138-116">**Général**</span><span class="sxs-lookup"><span data-stu-id="4b138-116">**General**</span></span>|<span data-ttu-id="4b138-117">Informations générales sur le message</span><span class="sxs-lookup"><span data-stu-id="4b138-117">Overview information about the message</span></span>|  
|<span data-ttu-id="4b138-118">**Contexte**</span><span class="sxs-lookup"><span data-stu-id="4b138-118">**Context**</span></span>|<span data-ttu-id="4b138-119">Propriétés de contexte associées à ce message</span><span class="sxs-lookup"><span data-stu-id="4b138-119">Context properties associated with this message</span></span>|  
|<span data-ttu-id="4b138-120">**Parties de message**</span><span class="sxs-lookup"><span data-stu-id="4b138-120">**Message Parts**</span></span>|<span data-ttu-id="4b138-121">Charge du document individuel contenu dans ce message.</span><span class="sxs-lookup"><span data-stu-id="4b138-121">Individual document payload contained within this message.</span></span> <span data-ttu-id="4b138-122">Chaque document peut être affiché sous forme textuelle ou binaire :</span><span class="sxs-lookup"><span data-stu-id="4b138-122">Each document can be viewed as either text or binary:</span></span><br /><br /> <span data-ttu-id="4b138-123">-L’affichage au Format texte affiche le contenu du message AS2 ou MDN sous forme lisible, comme dans un fichier texte EDI.</span><span class="sxs-lookup"><span data-stu-id="4b138-123">-   Text Format view shows the contents of the AS2 message or MDN in human-readable form, as in an EDI text file.</span></span> <span data-ttu-id="4b138-124">Cet affichage contient les en-têtes AS2, les codes de fin EDI et la charge EDI, chaque segment se trouvant sur une ligne distincte.</span><span class="sxs-lookup"><span data-stu-id="4b138-124">This view shows the AS2 headers, EDI trailers, and EDI payload, with each segment on a separate line.</span></span><br /><span data-ttu-id="4b138-125">-L’affichage au Format binaire présente le contenu du message AS2 ou MDN dans un format texte non délimité et une table des représentations hexadécimales de chaque caractère ASCII dans le message AS2 ou MDN.</span><span class="sxs-lookup"><span data-stu-id="4b138-125">-   Binary Format view shows the contents of the AS2 message or MDN in non-delimited text format and a table of the hexadecimal representations for each ASCII character in the AS2 message or MDN.</span></span>|
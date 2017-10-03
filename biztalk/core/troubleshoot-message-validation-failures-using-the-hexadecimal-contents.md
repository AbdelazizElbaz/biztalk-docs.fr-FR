---
title: "Dépannage des échecs de Validation de Message en affichant le contenu hexadécimal de Messages suspendus | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cf14cd9-2d4b-43a3-9738-52bfd879e1e4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f7dc0f24a85f206831e3706bd03f2206aaa2c15
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-message-validation-failures-by-viewing-the-hexadecimal-contents-of-suspended-messages"></a><span data-ttu-id="9567e-102">Dépannage des problèmes de validation de message par l'affichage du contenu hexadécimal des messages suspendus</span><span class="sxs-lookup"><span data-stu-id="9567e-102">Troubleshooting Message Validation Failures by Viewing the Hexadecimal Contents of Suspended Messages</span></span>
<span data-ttu-id="9567e-103">Si un message est suspendu en raison d'un échec de validation, consulter la représentation hexadécimale des parties du message peut permettre de déterminer la cause de l'échec.</span><span class="sxs-lookup"><span data-stu-id="9567e-103">If a message is suspended due to validation failures, it may be helpful to view the hexadecimal representation of the message parts to determine the cause of the validation failure.</span></span> <span data-ttu-id="9567e-104">Cette rubrique répertorie les étapes à suivre pour consulter la représentation hexadécimale des parties d'un message suspendu.</span><span class="sxs-lookup"><span data-stu-id="9567e-104">This topic lists steps that can be followed to view the hexadecimal representation of the parts of a suspended message.</span></span>  
  
## <a name="use-the-message-details-dialog-box-to-view-message-parts"></a><span data-ttu-id="9567e-105">Utilisation de la boîte de dialogue Détails sur le message pour afficher les parties du message</span><span class="sxs-lookup"><span data-stu-id="9567e-105">Use the Message Details dialog box to view message parts</span></span>  
 <span data-ttu-id="9567e-106">Suivez la procédure ci-dessous pour afficher la représentation hexadécimale des parties du message :</span><span class="sxs-lookup"><span data-stu-id="9567e-106">Follow these steps to view the hexadecimal representation of message parts:</span></span>  
  
1.  <span data-ttu-id="9567e-107">Utilisez le **requête** onglet dans la Console Administration de BizTalk pour retourner un jeu de résultats avec un ou plusieurs messages suspendus.</span><span class="sxs-lookup"><span data-stu-id="9567e-107">Use the **Query** tab in the BizTalk Administration Console to return a result set with one or more suspended messages.</span></span> <span data-ttu-id="9567e-108">Consultez [comment rechercher des Messages](../core/how-to-search-for-messages.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="9567e-108">See [How to Search for Messages](../core/how-to-search-for-messages.md) for more information.</span></span>  
  
2.  <span data-ttu-id="9567e-109">Double-cliquez sur le message suspendu qui vous intéresse pour afficher le **détails du Message** boîte de dialogue pour le message.</span><span class="sxs-lookup"><span data-stu-id="9567e-109">Double-click the suspended message that you want to investigate to display the **Message Details** dialog box for the message.</span></span>  
  
3.  <span data-ttu-id="9567e-110">Cliquez sur une partie de message dans le volet gauche de la **détails du Message** boîte de dialogue pour afficher la partie de message.</span><span class="sxs-lookup"><span data-stu-id="9567e-110">Click a message part in the left hand pane of the **Message Details** dialog box to display the message part.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9567e-111">Les messages peuvent comporter 0, 1 ou plusieurs parties.</span><span class="sxs-lookup"><span data-stu-id="9567e-111">Messages may have 0, 1 or many message parts.</span></span> <span data-ttu-id="9567e-112">La plupart du temps, ils en contiennent une seule, appelée « corps ».</span><span class="sxs-lookup"><span data-stu-id="9567e-112">Most often messages have single message part that is called "body".</span></span>  
  
4.  <span data-ttu-id="9567e-113">Cliquez sur le **binaire** onglet dans le volet de droite de la **détails du Message** boîte de dialogue pour afficher la représentation hexadécimale de la partie du message.</span><span class="sxs-lookup"><span data-stu-id="9567e-113">Click the **Binary** tab in the right hand pane of the **Message Details** dialog box to display the hexadecimal representation of the message part.</span></span>  
  
5.  <span data-ttu-id="9567e-114">Recherchez les points suivants dans la représentation hexadécimale :</span><span class="sxs-lookup"><span data-stu-id="9567e-114">Check the hexadecimal representation of characters in message parts for the following:</span></span>  
  
    -   <span data-ttu-id="9567e-115">Une marque d'ordre de tri manquante ou non valide.</span><span class="sxs-lookup"><span data-stu-id="9567e-115">Missing or invalid byte order mark.</span></span> <span data-ttu-id="9567e-116">Pour plus d’informations sur l’ordre d’octet marques consultez [http://go.microsoft.com/fwlink/?LinkId=196380](http://go.microsoft.com/fwlink/?LinkId=196380).</span><span class="sxs-lookup"><span data-stu-id="9567e-116">For more information about byte order marks see [http://go.microsoft.com/fwlink/?LinkId=196380](http://go.microsoft.com/fwlink/?LinkId=196380).</span></span>  
  
    -   <span data-ttu-id="9567e-117">Des différences de codage des sauts de ligne entre Unix et Windows.</span><span class="sxs-lookup"><span data-stu-id="9567e-117">Differences between the encoding of linebreaks in Unix and Windows.</span></span> <span data-ttu-id="9567e-118">Unix utilise le saut à la ligne hexadécimal (0A) pour indiquer le saut de ligne, tandis que Windows utilise à la fois le retour chariot hexadécimal (0D) et le saut à la ligne (0A).</span><span class="sxs-lookup"><span data-stu-id="9567e-118">Unix uses hex linefeed (0A) to indicate a line break where Windows uses both hex carriage return (0D) and linefeed (0A) to indicate a line break.</span></span>  
  
    -   <span data-ttu-id="9567e-119">Des caractères de contrôle non valides.</span><span class="sxs-lookup"><span data-stu-id="9567e-119">Invalid control character(s) in message parts.</span></span> <span data-ttu-id="9567e-120">Les caractères de contrôle qui ne s'affichent pas au format texte peuvent être visibles au format binaire.</span><span class="sxs-lookup"><span data-stu-id="9567e-120">Control characters in message parts that do not show up in the text view may be visible in the binary view.</span></span>  
  
    -   <span data-ttu-id="9567e-121">Des caractères nuls non valides au milieu d'une partie de message peuvent tronquer la partie de message.</span><span class="sxs-lookup"><span data-stu-id="9567e-121">Invalid nul character(s) in the middle of a message part can cause the message part to be truncated.</span></span> <span data-ttu-id="9567e-122">Le caractère nul est représenté par la valeur hexadécimale (00).</span><span class="sxs-lookup"><span data-stu-id="9567e-122">The nul character is represented as hex (00).</span></span>  
  
    -   <span data-ttu-id="9567e-123">Un décalage de caractères non valide dans les fichiers plats positionnels.</span><span class="sxs-lookup"><span data-stu-id="9567e-123">Invalid character offset in positional flat files.</span></span> <span data-ttu-id="9567e-124">Affichez la représentation hexadécimale d'une partie de message pour consulter le décalage de données dans un fichier plat positionnel.</span><span class="sxs-lookup"><span data-stu-id="9567e-124">Display the hexadecimal representation of a message part to view the offset of data in a positional flat file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9567e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9567e-125">See Also</span></span>  
 [<span data-ttu-id="9567e-126">Enquête sur les échecs de messages, de Port et d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="9567e-126">Investigating Orchestration, Port, and Message Failures</span></span>](../core/investigating-orchestration-port-and-message-failures.md)
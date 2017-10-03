---
title: "Émission et échange un Ticket d’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0323a6-cc31-460d-b64d-b4d8142c3855
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9988eedb545b3b1a348a5de6275b176abe2be7e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="issuing-and-redeeming-a-single-sign-on-ticket"></a><span data-ttu-id="30306-102">Émission et échange un Ticket d’authentification unique</span><span class="sxs-lookup"><span data-stu-id="30306-102">Issuing and Redeeming a Single Sign-On Ticket</span></span>
<span data-ttu-id="30306-103">Après avoir lié un utilisateur et une application associée, vous pouvez émettre des tickets pour assurer la sécurité tout en maintenant les communications.</span><span class="sxs-lookup"><span data-stu-id="30306-103">After you link a user and an affiliate application, you can issue tickets to help ensure security while maintaining communications.</span></span> <span data-ttu-id="30306-104">Seule l’authentification sur la création de tickets fonctionne exactement comme les autres technologies de gestion de tickets : avant d’envoyer le message hors tension, vous ajoutez le ticket d’authentification unique pour le message sous forme de chaîne.</span><span class="sxs-lookup"><span data-stu-id="30306-104">Single Sign-On ticketing works just like other ticketing technologies: before sending the message off, you append the Single Sign-On ticket to the message as a string.</span></span> <span data-ttu-id="30306-105">Le serveur reçoit votre message, décode le ticket et utilise l'information de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="30306-105">The server receives your message, decodes the ticket, and uses the information as appropriate.</span></span>  
  
### <a name="to-issue-a-single-sign-on-ticket"></a><span data-ttu-id="30306-106">Pour émettre un ticket d'authentification unique</span><span class="sxs-lookup"><span data-stu-id="30306-106">To issue a Single Sign-On ticket</span></span>  
  
1.  <span data-ttu-id="30306-107">Créez un objet ticket en appelant I`SSOTicket`.</span><span class="sxs-lookup"><span data-stu-id="30306-107">Create a new ticket object with a call to I`SSOTicket`.</span></span>  
  
2.  <span data-ttu-id="30306-108">Émettez le ticket en appelant I`SSOTicket.IssueTicket`.</span><span class="sxs-lookup"><span data-stu-id="30306-108">Issue the ticket with a call to I`SSOTicket.IssueTicket`.</span></span>  
  
### <a name="to-redeem-a-single-sign-on-ticket"></a><span data-ttu-id="30306-109">Pour échanger un ticket d'authentification unique</span><span class="sxs-lookup"><span data-stu-id="30306-109">To redeem a Single Sign-On ticket</span></span>  
  
1.  <span data-ttu-id="30306-110">Créez un objet ticket en appelant I`SSOTicket`.</span><span class="sxs-lookup"><span data-stu-id="30306-110">Create a new ticket object with a call to I`SSOTicket`.</span></span>  
  
2.  <span data-ttu-id="30306-111">Échangez le ticket en appelant I`SSOTicket.RedeemTicket`.</span><span class="sxs-lookup"><span data-stu-id="30306-111">Redeem the ticket with a call to I`SSOTicket.RedeemTicket`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30306-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30306-112">See Also</span></span>  
 [<span data-ttu-id="30306-113">Programmation avec Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="30306-113">Programming with Enterprise Single Sign-On</span></span>](../core/programming-with-enterprise-single-sign-on.md)
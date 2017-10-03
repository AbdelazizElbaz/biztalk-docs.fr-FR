---
title: "Comment créer un Port1 envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating send ports
- send ports, creating
ms.assetid: bf32e9f5-ebed-43d2-b9a9-6ab91925d973
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61c82b199f7b8686556f2cbb53a90b0d4b59536e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-send-port"></a><span data-ttu-id="ec45c-102">Comment créer un Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="ec45c-102">How to Create a Send Port</span></span>
<span data-ttu-id="ec45c-103">La procédure suivante permet de créer des ports d'envoi BizTalk Server pour JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="ec45c-103">Use the following procedure to create BizTalk Server send ports for JD Edwards EnterpriseOne.</span></span>  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="ec45c-104">Pour créer un port d’envoi</span><span class="sxs-lookup"><span data-stu-id="ec45c-104">To create a send port</span></span>  
  
1.  <span data-ttu-id="ec45c-105">Cliquez avec le bouton droit sur le nœud Ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="ec45c-105">Right-click the Send Ports node.</span></span>  
  
2.  <span data-ttu-id="ec45c-106">Cliquez sur **ajouter le Port d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="ec45c-106">Click **Add Send Port**.</span></span>  
  
3.  <span data-ttu-id="ec45c-107">Dans le **créer un Port d’envoi** boîte de dialogue, sélectionnez **Port statique avec sollicitation-réponse** à partir de la **spécifier le type de Port d’envoi** liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ec45c-107">In the **Create New Send Port** dialog box, select **Static Solicit-Response Port** from the **Specify the type of Send Port** list, and click **OK**.</span></span>  
  
     <span data-ttu-id="ec45c-108">Le **statique propriétés du Port d’envoi avec sollicitation-réponse** fenêtre s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="ec45c-108">The **Static Solicit-Response Send Port Properties** window opens.</span></span>  
  
4.  <span data-ttu-id="ec45c-109">Tapez un nom pour le port d’envoi, par exemple, `SSOSendToJDEEntOne`.</span><span class="sxs-lookup"><span data-stu-id="ec45c-109">Type a name for the send port, for example, `SSOSendToJDEEntOne`.</span></span>  
  
5.  <span data-ttu-id="ec45c-110">Cliquez sur **Transport** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="ec45c-110">Click **Transport** in the left pane.</span></span>  
  
6.  <span data-ttu-id="ec45c-111">Cliquez sur **Type de Transport**, puis sélectionnez **JDEEntOne**.</span><span class="sxs-lookup"><span data-stu-id="ec45c-111">Click **Transport Type**, and select **JDEEntOne**.</span></span>  
  
7.  <span data-ttu-id="ec45c-112">Sélectionnez le **adresse (URI)**, puis cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="ec45c-112">Select the **Address (URI)**, and click the ellipsis (…) button.</span></span>  
  
     <span data-ttu-id="ec45c-113">JD Edwards EnterpriseOne **propriétés du Transport** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="ec45c-113">The JD Edwards EnterpriseOne **Transport Properties** dialog box appears.</span></span>  
  
8.  <span data-ttu-id="ec45c-114">Type `myJDEEntOneSSO` pour le **nom système logique**.</span><span class="sxs-lookup"><span data-stu-id="ec45c-114">Type `myJDEEntOneSSO` for the **Logical System Name**.</span></span>  
  
9. <span data-ttu-id="ec45c-115">Sélectionnez **Oui** pour **utiliser l’authentification unique**.</span><span class="sxs-lookup"><span data-stu-id="ec45c-115">Select **Yes** for **Use SSO**.</span></span>  
  
10. <span data-ttu-id="ec45c-116">Dans la liste déroulante, sélectionnez l'application associée à authentification unique que vous avez créée pour représenter le système JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="ec45c-116">In the drop-down list, select the Single Sign-On (SSO) affiliate application that you created to represent the JD Edwards EnterpriseOne system.</span></span>  
  
     <span data-ttu-id="ec45c-117">Cliquez sur **OK** pour confirmer les informations que vous avez entré.</span><span class="sxs-lookup"><span data-stu-id="ec45c-117">Click **OK** to confirm the information you entered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec45c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec45c-118">See Also</span></span>  
 <span data-ttu-id="ec45c-119">[Création d’Applications associées](../core/creating-affiliate-applications4.md) </span><span class="sxs-lookup"><span data-stu-id="ec45c-119">[Creating Affiliate Applications](../core/creating-affiliate-applications4.md) </span></span>  
 [<span data-ttu-id="ec45c-120">À l’aide de l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="ec45c-120">Using Single Sign-On</span></span>](../core/using-single-sign-on1.md)
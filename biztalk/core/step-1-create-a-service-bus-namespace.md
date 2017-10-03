---
title: "Étape 1 : Créer un Namespace de Bus de Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ede1ac50-bbfb-4aeb-8217-1877ae218f89
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4d7630316f72fd63bac5ce7127b5451683e2f97
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-create-a-service-bus-namespace"></a><span data-ttu-id="c0b3c-102">Étape 1 : Créer un Namespace de Bus de Service</span><span class="sxs-lookup"><span data-stu-id="c0b3c-102">Step 1: Create a Service Bus Namespace</span></span>
<span data-ttu-id="c0b3c-103">Dans cette étape, vous allez créer un [!INCLUDE[winazure](../includes/winazure-md.md)] [!INCLUDE[sb](../includes/sb-md.md)] espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c0b3c-103">In this step, you create a [!INCLUDE[winazure](../includes/winazure-md.md)][!INCLUDE[sb](../includes/sb-md.md)] namespace.</span></span> <span data-ttu-id="c0b3c-104">Vous allez utiliser cet espace de noms pour héberger un point de terminaison de relais afin de recevoir des notifications d'opportunité de Salesforce.</span><span class="sxs-lookup"><span data-stu-id="c0b3c-104">You will use this namespace to host a relay endpoint for receiving opportunity notifications from Salesforce.</span></span> <span data-ttu-id="c0b3c-105">Plus tard dans le processus de création de cette solution, vous allez utiliser ce point de terminaison de relais pour recevoir le message de notification dans un système [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0b3c-105">Later in the process of creating this solution, you will use this relay endpoint to receive the notification message into a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system.</span></span>  
  
### <a name="to-create-a-includesbincludessb-mdmd-namespace"></a><span data-ttu-id="c0b3c-106">Pour créer un espace de noms [!INCLUDE[sb](../includes/sb-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0b3c-106">To create a [!INCLUDE[sb](../includes/sb-md.md)] namespace</span></span>  
  
1.  <span data-ttu-id="c0b3c-107">Ouvrez une session sur [http://manage.windowsazure.com](http://manage.windowsazure.com) à l’aide de votre compte Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c0b3c-107">Log on to [http://manage.windowsazure.com](http://manage.windowsazure.com) using your Microsoft account.</span></span>  
  
2.  <span data-ttu-id="c0b3c-108">Au bas de la page, cliquez sur **nouveau**, **des Services d’application**, **relais Service Bus**, puis **création rapide**.</span><span class="sxs-lookup"><span data-stu-id="c0b3c-108">At the bottom of the page, click **New**, **App Services**, **Service Bus Relay**, and then **Quick Create**.</span></span>  
  
3.  <span data-ttu-id="c0b3c-109">Entrez l’espace de noms `BtsSalesforce` et sélectionnez une région proche de votre emplacement géographique actuel.</span><span class="sxs-lookup"><span data-stu-id="c0b3c-109">Enter the namespace as `BtsSalesforce` and select a region closest to your current geographical location.</span></span> <span data-ttu-id="c0b3c-110">Cliquez sur **créer un relais**.</span><span class="sxs-lookup"><span data-stu-id="c0b3c-110">Click **Create a Relay**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="c0b3c-111">Cet espace de noms doit être globalement unique.</span><span class="sxs-lookup"><span data-stu-id="c0b3c-111">This namespace must be globally unique.</span></span> <span data-ttu-id="c0b3c-112">Ainsi, vous devez utiliser un espace de noms autre que celui mentionné dans ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="c0b3c-112">So, you must use a namespace other than one mentioned in this tutorial.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c0b3c-113">Notez que le relais n'est pas créé dans le cadre de l'opération, seul l'espace l'est.</span><span class="sxs-lookup"><span data-stu-id="c0b3c-113">Note that the relay is not created as part of the operation, only the namespace is.</span></span> <span data-ttu-id="c0b3c-114">Le point de terminaison de relais est créé ultérieurement dans ce didacticiel lorsque nous configurons un emplacement de réception pour le **SB-Messaging** carte.</span><span class="sxs-lookup"><span data-stu-id="c0b3c-114">The relay endpoint is created later in this tutorial when we configure a receive location for the **SB-Messaging** adapter.</span></span>  
  
4.  <span data-ttu-id="c0b3c-115">Une fois l’espace de noms est créé, l’état est défini sur **Active**.</span><span class="sxs-lookup"><span data-stu-id="c0b3c-115">After the namespace is created, the status is set to **Active**.</span></span> <span data-ttu-id="c0b3c-116">Une fois que l’état est actif, vous pouvez sélectionner l’espace de noms et cliquez sur **clé d’accès** au bas de la page pour obtenir plus d’informations sur la façon de se connecter à la **BtsSalesforce** espace de noms, y compris les valeurs de **Utilisateur par défaut** et **clé par défaut**.</span><span class="sxs-lookup"><span data-stu-id="c0b3c-116">Once the status is active, you can select the namespace and click **Access Key** at the bottom of the page to get details on how to connect to the **BtsSalesforce** namespace, including the values for **Default User** and **Default Key**.</span></span> <span data-ttu-id="c0b3c-117">Vous aurez besoin de ces détails ultérieurement dans ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="c0b3c-117">You will need these details later in the tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0b3c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0b3c-118">See Also</span></span>  
 [<span data-ttu-id="c0b3c-119">Didacticiel 6 : Intégration de BizTalk Server 2013 avec Salesforce</span><span class="sxs-lookup"><span data-stu-id="c0b3c-119">Tutorial 6: Integrating BizTalk Server 2013 with Salesforce</span></span>](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)
---
title: "Comment créer des Ports d’envoi pour PeopleSoft Enterprise | Documents Microsoft"
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
ms.assetid: 374261ce-2cb5-4193-a0a2-658f989b2c60
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b6b5caa44976aec7a4afb8e0eccf5b1f8904111
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-peoplesoft-enterprise"></a><span data-ttu-id="48cf5-102">Création des ports d'envoi pour PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="48cf5-102">How to Create Send Ports for PeopleSoft Enterprise</span></span>
<span data-ttu-id="48cf5-103">Suivez les étapes ci-après pour créer un port d'envoi à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="48cf5-103">Follow these steps to create a send port using BizTalk Server Administration Console.</span></span>  
  
## <a name="creating-a-send-port"></a><span data-ttu-id="48cf5-104">Création d'un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="48cf5-104">Creating a Send Port</span></span>  
  
#### <a name="to-create-a-send-port"></a><span data-ttu-id="48cf5-105">Pour créer un port d’envoi</span><span class="sxs-lookup"><span data-stu-id="48cf5-105">To create a send port</span></span>  
  
1.  <span data-ttu-id="48cf5-106">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="48cf5-106">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="48cf5-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="48cf5-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="48cf5-108">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="48cf5-108">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="48cf5-109">Tapez un nom pour le port d’envoi, par exemple, `SSOSendToPeopleSoft`.</span><span class="sxs-lookup"><span data-stu-id="48cf5-109">Type a name for the send port, for example, `SSOSendToPeopleSoft`.</span></span>  
  
    2.  <span data-ttu-id="48cf5-110">À partir de la **Type** la liste déroulante, sélectionnez **PeopleSoft**.</span><span class="sxs-lookup"><span data-stu-id="48cf5-110">From the **Type** drop-down list, select **PeopleSoft**.</span></span>  
  
    3.  <span data-ttu-id="48cf5-111">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="48cf5-111">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="48cf5-112">Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="48cf5-112">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="48cf5-113">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="48cf5-113">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
    6.  <span data-ttu-id="48cf5-114">Cliquez sur **configurer** pour configurer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="48cf5-114">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="48cf5-115">Dans le **propriétés du Transport PeopleSoft** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="48cf5-115">In the **PeopleSoft Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="48cf5-116">Développez **propriétés obligatoires de l’adaptateur**, puis entrez **chemin d’accès au serveur d’Application**, **JAVA_HOME**, **nom d’utilisateur**,  **mot de passe**et le fichier Jar pour la connexion au système Peoplesoft.</span><span class="sxs-lookup"><span data-stu-id="48cf5-116">Expand **Adapter Required Properties**, and enter **Application Server Path**, **JAVA_HOME**, **user name**, **password**, and the Jar file for connecting into the Peoplesoft system.</span></span>  
  
         <span data-ttu-id="48cf5-117">Il n'est pas nécessaire de définir les informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="48cf5-117">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="48cf5-118">Dans la liste, sélectionnez l'application associée SSO que vous avez créée pour représenter le système PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="48cf5-118">In the list, select the SSO affiliate application you created to represent the PeopleSoft system.</span></span>  
  
    3.  <span data-ttu-id="48cf5-119">Pour **utiliser SSO**, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="48cf5-119">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="48cf5-120">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="48cf5-120">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="48cf5-121">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="48cf5-121">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48cf5-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48cf5-122">See Also</span></span>  
 [<span data-ttu-id="48cf5-123">Création de gestionnaires d’envoi PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="48cf5-123">Creating PeopleSoft Send Handlers</span></span>](../core/creating-peoplesoft-send-handlers.md)
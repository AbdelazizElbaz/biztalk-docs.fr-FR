---
title: "Étape 2 : Création de Ports pour le prix de 3A2 de Contoso et le scénario de requête-réponse de disponibilité à l’aide de l’Explorateur BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: private process tutorial, creating ports
ms.assetid: e0b12a96-e799-47ac-8293-7de10662bdf0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64101a31b1d1ea9c7af00471c5d764a1d8cfe598
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-creating-ports-for-the-contoso-3a2-price-and-availability-queryresponse-scenario"></a><span data-ttu-id="fd03c-102">Étape 2 : Création de Ports pour le prix 3A2 de Contoso et le scénario de requête/réponse de disponibilité</span><span class="sxs-lookup"><span data-stu-id="fd03c-102">Step 2: Creating Ports for the Contoso 3A2 Price and Availability Query/Response Scenario</span></span>
<span data-ttu-id="fd03c-103">Dans cette étape, vous créez des ports d’envoi à l’aide de l’adaptateur SQL fourni par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="fd03c-103">In this step, you create send ports using the SQL adapter provided by BizTalk Server.</span></span> <span data-ttu-id="fd03c-104">Vous utilisez le port SQL pour envoyer et recevoir la réponse 3A2 en matière de prix et de disponibilité, à destination et en provenance du système ERP de Contoso.</span><span class="sxs-lookup"><span data-stu-id="fd03c-104">You use the SQL port for sending and receiving the 3A2 Price and Availability response to and from the ERP system for Contoso.</span></span>  
  
### <a name="to-configure-a-send-port-using-the-sql-adapter"></a><span data-ttu-id="fd03c-105">Pour configurer un port d'envoi à l'aide de l'adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="fd03c-105">To configure a send port using the SQL adapter</span></span>  
  
1.  <span data-ttu-id="fd03c-106">Dans Visual Studio, sur le **vue** menu, cliquez sur **l’Explorateur BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="fd03c-106">In Visual Studio, on the **View** menu, click **BizTalk Explorer**.</span></span>  
  
2.  <span data-ttu-id="fd03c-107">Dans l'Explorateur BizTalk, cliquez avec le bouton droit sur **Ports d'envoi**, puis cliquez sur **Ajouter un port d'envoi**.</span><span class="sxs-lookup"><span data-stu-id="fd03c-107">In BizTalk Explorer, right-click **Send Ports**, and then click **Add Send Port**.</span></span>  
  
3.  <span data-ttu-id="fd03c-108">Dans la boîte de dialogue Créer un groupe de ports d'envoi, sélectionnez **Port statique avec sollicitation-réponse** dans la liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fd03c-108">In the Create New Send Port dialog box, select **Static Solicit-Response Port** from the drop-down list, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="fd03c-109">Dans la zone **Nom** de la boîte de dialogue Propriétés du port d'envoi statique avec sollicitation-réponse, tapez **3A2SQLReqResponseSendPort**.</span><span class="sxs-lookup"><span data-stu-id="fd03c-109">In the Static Solicit-Response Send Port Properties dialog box, in the **Name** box, type **3A2SQLReqResponseSendPort**.</span></span>  
  
5.  <span data-ttu-id="fd03c-110">Dans la fenêtre Propriétés, sous le titre **Général** , sélectionnez **SQL** en tant que **Type de transport**.</span><span class="sxs-lookup"><span data-stu-id="fd03c-110">In the Properties window under the **General** heading, select **SQL** as the **Transport Type**.</span></span>  
  
6.  <span data-ttu-id="fd03c-111">Dans la zone **Adresse (URI)** , cliquez sur le bouton de sélection (**…**).</span><span class="sxs-lookup"><span data-stu-id="fd03c-111">In the **Address URI** box, click the ellipsis button (**…**).</span></span>  
  
7.  <span data-ttu-id="fd03c-112">Dans la boîte de dialogue Propriétés du transport SQL, cliquez sur le bouton de sélection (**...**) en regard de la zone **Chaîne de connexion** .</span><span class="sxs-lookup"><span data-stu-id="fd03c-112">In the SQL Transport Properties dialog box, click the ellipsis button (**…**) next to the **Connection String** box.</span></span>  
  
8.  <span data-ttu-id="fd03c-113">Dans la boîte de dialogue Propriétés des liaisons de données, dans la zone **Sélectionnez un serveur ou entrez un nom de serveur** , tapez **localhost**.</span><span class="sxs-lookup"><span data-stu-id="fd03c-113">In the Data Link Properties dialog box, in the **Select or enter a server name** box, type **localhost**.</span></span>  
  
9. <span data-ttu-id="fd03c-114">Sélectionnez **Utiliser la sécurité intégrée de Windows NT**.</span><span class="sxs-lookup"><span data-stu-id="fd03c-114">Select **Use Windows NT Integrated security**.</span></span>  
  
10. <span data-ttu-id="fd03c-115">Dans la zone **Sélectionnez la base de données sur le serveur** , sélectionnez **Contoso**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fd03c-115">In the **Select the database on the server** box, select **Contoso**, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="fd03c-116">Dans la boîte de dialogue Propriétés du transport SQL, dans la zone **Espace de noms cible du document** , tapez **http://Contoso.com/Price**.</span><span class="sxs-lookup"><span data-stu-id="fd03c-116">In the SQL Transport Properties dialog box, in the **Document Target Namespace** box, type **http://Contoso.com/Price**.</span></span>  
  
12. <span data-ttu-id="fd03c-117">Dans la zone **Nom de l'élément racine du document de réponse** , tapez **rootPriceResponse**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fd03c-117">In the **Response Document Root Element Name** box, type **rootPriceResponse**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="fd03c-118">Dans le volet gauche de la boîte de dialogue Propriétés du port d'envoi statique avec sollicitation-réponse, cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="fd03c-118">In the left pane of the Static Solicit-Response Send Port Properties dialog box, click **Send**.</span></span>  
  
14. <span data-ttu-id="fd03c-119">Dans la boîte de dialogue Propriétés du port d'envoi statique avec sollicitation-réponse-Configurations-Envoi-Général, dans la zone **Pipeline d'envoi** , sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="fd03c-119">In the Static Solicit-Response Send Port Properties-Configurations-Send-General dialog box, in the **Send Pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
15. <span data-ttu-id="fd03c-120">Dans la zone **Pipeline de réception** , sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLReceive**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="fd03c-120">In the **Receive Pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.XMLReceive**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="fd03c-121">Dans l'Explorateur BizTalk, cliquez avec le bouton droit sur **3A2SQLReqResponseSendPort**, puis cliquez sur **Inscrire**.</span><span class="sxs-lookup"><span data-stu-id="fd03c-121">In BizTalk Explorer, right-click **3A2SQLReqResponseSendPort**, and then click **Enlist**.</span></span> <span data-ttu-id="fd03c-122">Cliquez avec le bouton droit une fois de plus, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="fd03c-122">Right-click it again, and click **Start**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd03c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd03c-123">See Also</span></span>  
 [<span data-ttu-id="fd03c-124">Création et modification du processus privé pour Contoso</span><span class="sxs-lookup"><span data-stu-id="fd03c-124">Creating and Modifying the Private Process for Contoso</span></span>](creating-and-modifying-the-private-process-for-contoso.md)
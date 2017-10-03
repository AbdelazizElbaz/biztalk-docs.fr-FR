---
title: "Configuration des paramètres HTTP des MDN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c877e85-7887-43a9-9fd4-0853b573213f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f74ba2eaf11e8beed3e28d10beb9f95b2f0f6194
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-http-settings-for-mdns"></a><span data-ttu-id="b7b95-102">Configuration des paramètres HTTP des MDN</span><span class="sxs-lookup"><span data-stu-id="b7b95-102">Configuring HTTP Settings for MDNs</span></span>
<span data-ttu-id="b7b95-103">Vous pouvez spécifier les propriétés attendues par le serveur Web qui reçoit les MDN dans les paramètres HTTP des MDN.</span><span class="sxs-lookup"><span data-stu-id="b7b95-103">As part of MDN-related HTTP settings, you can specify the properties expected by the Web server that receives the MDNs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b7b95-104">Toutes les propriétés sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.</span><span class="sxs-lookup"><span data-stu-id="b7b95-104">All the properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  <span data-ttu-id="b7b95-105">Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers.</span><span class="sxs-lookup"><span data-stu-id="b7b95-105">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="b7b95-106">Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="b7b95-106">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b7b95-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b7b95-107">Prerequisites</span></span>  
 <span data-ttu-id="b7b95-108">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7b95-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-mdn-related-http-settings"></a><span data-ttu-id="b7b95-109">Pour configurer les paramètres HTTP des MDN</span><span class="sxs-lookup"><span data-stu-id="b7b95-109">To configure MDN-related HTTP settings</span></span>  
  
1.  <span data-ttu-id="b7b95-110">Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md).</span><span class="sxs-lookup"><span data-stu-id="b7b95-110">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="b7b95-111">Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b7b95-111">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b7b95-112">Sous l’onglet accord unidirectionnel, sous **paramètres d’hôte Local** , cliquez sur **paramètres HTTP des MDN**.</span><span class="sxs-lookup"><span data-stu-id="b7b95-112">On a one-way agreement tab, under **Local Host Settings** section, click **HTTP Settings for MDNs**.</span></span>  
  
3.  <span data-ttu-id="b7b95-113">Sélectionnez le **incompatibilité du nom du certificat SSL ignorer** case à cocher pour vous assurer que si le nom du serveur ne correspond pas à qui le certificat SSL a été généré pour le nom du serveur, la connexion SSL serait quand même être acceptés.</span><span class="sxs-lookup"><span data-stu-id="b7b95-113">Select the **Ignore SSL Certificate Name mismatch** check box to ensure that if the server name does not match the server name that the SSL certificate was generated for, the SSL connection would still be accepted.</span></span>  
  
4.  <span data-ttu-id="b7b95-114">Cliquez sur **HTTP expect 100-continuer** pour définir l’en-tête HTTP Expect sur 100-continue, ce qui indique que les données publiées ne pas être inclus dans la requête HTTP initiale, mais attend que le serveur demande le contenu.</span><span class="sxs-lookup"><span data-stu-id="b7b95-114">Click **HTTP expect 100 continue** to set the HTTP Expect header to 100-continue, which specifies that the posted data not be included in the initial HTTP request, but waits for the server to request the content.</span></span>  
  
5.  <span data-ttu-id="b7b95-115">Cliquez sur **garder la connexion HTTP active** pour demander qu’une connexion HTTP reste active après un cycle de demande et de réponse a été effectué.</span><span class="sxs-lookup"><span data-stu-id="b7b95-115">Click **Keep HTTP connection alive** to request that an HTTP connection be kept alive after a request and response cycle has been completed.</span></span>  
  
6.  <span data-ttu-id="b7b95-116">Cliquez sur **dérouler les en-têtes HTTP** pour dérouler l’en-tête content-type HTTP sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="b7b95-116">Click **Unfold HTTP headers** to unfold the HTTP content-type header into a single line.</span></span>  
  
7.  <span data-ttu-id="b7b95-117">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="b7b95-117">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b95-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7b95-118">See Also</span></span>  
 [<span data-ttu-id="b7b95-119">Configuration des paramètres de l’hôte Local (AS2)</span><span class="sxs-lookup"><span data-stu-id="b7b95-119">Configuring Local Host Settings (AS2)</span></span>](../core/configuring-local-host-settings-as2.md)
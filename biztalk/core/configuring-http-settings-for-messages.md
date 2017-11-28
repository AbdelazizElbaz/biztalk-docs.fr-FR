---
title: "Configuration des paramètres HTTP des Messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ed400f1-561d-4812-adf1-20e4300fd048
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d15ebb5ff5be6678c4dc2aee3f9333f36c75c89f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-http-settings-for-messages"></a><span data-ttu-id="d03b3-102">Configuration des paramètres HTTP des Messages</span><span class="sxs-lookup"><span data-stu-id="d03b3-102">Configuring HTTP Settings for Messages</span></span>
<span data-ttu-id="d03b3-103">Vous pouvez spécifier les propriétés attendues par le serveur Web qui reçoit les messages AS2 dans les paramètres HTTP des messages.</span><span class="sxs-lookup"><span data-stu-id="d03b3-103">As part of message-related HTTP settings, you can specify the properties expected by the Web server that receives AS2 messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d03b3-104">Aucuns propriétés ne sont désactivées sur **tiers A -> tiers B** onglet d’accord unidirectionnel si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher pour le tiers A. Toutefois, toutes les propriétés sont désactivées sur la même page dans le **tiers B -> tiers A** onglet si vous avez sélectionné la case à cocher lors de la création du tiers A.</span><span class="sxs-lookup"><span data-stu-id="d03b3-104">No properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are disabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d03b3-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d03b3-105">Prerequisites</span></span>  
 <span data-ttu-id="d03b3-106">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d03b3-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-message-related-http-settings"></a><span data-ttu-id="d03b3-107">Pour configurer les paramètres HTTP des messages</span><span class="sxs-lookup"><span data-stu-id="d03b3-107">To configure message-related HTTP settings</span></span>  
  
1.  <span data-ttu-id="d03b3-108">Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md).</span><span class="sxs-lookup"><span data-stu-id="d03b3-108">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="d03b3-109">Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d03b3-109">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="d03b3-110">Sous l’onglet accord unidirectionnel, sous **paramètres d’hôte Local** , cliquez sur **paramètres HTTP des Messages**.</span><span class="sxs-lookup"><span data-stu-id="d03b3-110">On a one-way agreement tab, under **Local Host Settings** section, click **HTTP Settings for Messages**.</span></span>  
  
3.  <span data-ttu-id="d03b3-111">Sélectionnez le **incompatibilité du nom du certificat SSL ignorer** case à cocher pour vous assurer que si le nom du serveur ne correspond pas à qui le certificat SSL a été généré pour le nom du serveur, la connexion SSL serait quand même être acceptés.</span><span class="sxs-lookup"><span data-stu-id="d03b3-111">Select the **Ignore SSL Certificate Name mismatch** check box to ensure that if the server name does not match the server name that the SSL certificate was generated for, the SSL connection would still be accepted.</span></span>  
  
4.  <span data-ttu-id="d03b3-112">Cliquez sur **HTTP expect 100-continuer** pour définir l’en-tête HTTP Expect sur 100-continue, ce qui indique que les données publiées ne pas être inclus dans la requête HTTP initiale, mais attend que le serveur demande le contenu.</span><span class="sxs-lookup"><span data-stu-id="d03b3-112">Click **HTTP expect 100 continue** to set the HTTP Expect header to 100-continue, which specifies that the posted data not be included in the initial HTTP request, but waits for the server to request the content.</span></span>  
  
5.  <span data-ttu-id="d03b3-113">Cliquez sur **garder la connexion HTTP active** pour demander qu’une connexion HTTP reste active après un cycle de demande et de réponse a été effectué.</span><span class="sxs-lookup"><span data-stu-id="d03b3-113">Click **Keep HTTP connection alive** to request that an HTTP connection be kept alive after a request and response cycle has been completed.</span></span>  
  
6.  <span data-ttu-id="d03b3-114">Cliquez sur **dérouler les en-têtes HTTP** pour dérouler l’en-tête content-type HTTP sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="d03b3-114">Click **Unfold HTTP headers** to unfold the HTTP content-type header into a single line.</span></span>  
  
7.  <span data-ttu-id="d03b3-115">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="d03b3-115">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d03b3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d03b3-116">See Also</span></span>  
 [<span data-ttu-id="d03b3-117">Configuration des paramètres de l’hôte Local (AS2)</span><span class="sxs-lookup"><span data-stu-id="d03b3-117">Configuring Local Host Settings (AS2)</span></span>](../core/configuring-local-host-settings-as2.md)
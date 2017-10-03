---
title: "Configuration des paramètres généraux de l’hôte Local (AS2) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 980daac2-8387-44cc-ae55-38639f759668
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de5e5c076e6b245e4a662f8132d027e927df6142
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-general-local-host-settings-as2"></a><span data-ttu-id="b0d41-102">Configuration des paramètres généraux de l'hôte local (AS2)</span><span class="sxs-lookup"><span data-stu-id="b0d41-102">Configuring General Local Host Settings (AS2)</span></span>
<span data-ttu-id="b0d41-103">Dans les paramètres généraux de l'hôte local, vous pouvez spécifier le type de contenu des messages AS2 et si le nom du fichier est conservé dans l'en-tête du message AS2.</span><span class="sxs-lookup"><span data-stu-id="b0d41-103">As part of the local host general settings, you can specify the content type of the AS2 messages and whether the file name is preserved as part of the AS2 message header.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b0d41-104">Toutes les propriétés sont désactivées dans cette page si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.</span><span class="sxs-lookup"><span data-stu-id="b0d41-104">All the properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  <span data-ttu-id="b0d41-105">Cependant, les propriétés seront désactivées uniquement sous l'onglet d'accord unidirectionnel qui correspond aux propriétés des échanges envoyés par le tiers.</span><span class="sxs-lookup"><span data-stu-id="b0d41-105">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="b0d41-106">Par exemple, si vous créez deux tiers tiers A et tiers B et pour le tiers A, vous avez désactivé la case à cocher, la liste des propriétés ci-dessus sont désactivés sur le **tiers A -> tiers B** onglet d’accord unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="b0d41-106">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b0d41-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b0d41-107">Prerequisites</span></span>  
 <span data-ttu-id="b0d41-108">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0d41-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-the-general-settings"></a><span data-ttu-id="b0d41-109">Pour configurer les paramètres généraux</span><span class="sxs-lookup"><span data-stu-id="b0d41-109">To configure the general settings</span></span>  
  
1.  <span data-ttu-id="b0d41-110">Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md).</span><span class="sxs-lookup"><span data-stu-id="b0d41-110">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="b0d41-111">Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b0d41-111">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b0d41-112">Sous l’onglet accord unidirectionnel, sous **paramètres d’hôte Local** , cliquez sur **général**.</span><span class="sxs-lookup"><span data-stu-id="b0d41-112">On a one-way agreement tab, under **Local Host Settings** section, click **General**.</span></span>  
  
3.  <span data-ttu-id="b0d41-113">Sélectionnez le **vérifier la liste de révocation Certification avant d’envoyer le message** case à cocher pour déterminer si le certificat à utiliser pour signer un message sortant a été inclus dans la liste de révocation de Certification, qui indique qu’il a été révoqué, ou si la date d’expiration est passée.</span><span class="sxs-lookup"><span data-stu-id="b0d41-113">Select the **Check Certification Revocation List before sending the message** check box to determine whether the certificate to be used in signing an outgoing messages has been included in the Certification Revocation List, indicating that it has been revoked, or whether the expiration date has passed.</span></span> <span data-ttu-id="b0d41-114">Le cas échéant, BizTalk Server ne chiffre pas le message, mais l'interrompt.</span><span class="sxs-lookup"><span data-stu-id="b0d41-114">If so, BizTalk Server will not encrypt the message, but will suspend it.</span></span> <span data-ttu-id="b0d41-115">Si cette propriété est désactivée, BizTalk Server ne procédera pas à cette vérification.</span><span class="sxs-lookup"><span data-stu-id="b0d41-115">If this property is cleared, BizTalk Server will not perform this check.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b0d41-116">L'extraction et la recherche d'un certificat dans la liste de révocation des certificats nécessitent un certain délai.</span><span class="sxs-lookup"><span data-stu-id="b0d41-116">There is a latency involved with retrieving and searching the certificate revocation list.</span></span>  
  
4.  <span data-ttu-id="b0d41-117">Pour **par défaut du type de contenu**, sélectionnez le type de contenu par défaut que le tiers doit utiliser pour un message AS2 sortant.</span><span class="sxs-lookup"><span data-stu-id="b0d41-117">For **Default content type**, select the default content type that the party must use for an outgoing AS2 message.</span></span> <span data-ttu-id="b0d41-118">Si le `ContentType` propriété est définie dans le contexte pour une partie du corps de message, que le paramètre est utilisé pour générer le message sortant ; sinon, la valeur de cet **par défaut du type de contenu** propriété est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b0d41-118">If the `ContentType` property is set in the context for a message body part, that setting is used to generate the outgoing message; otherwise, the value of this **Default content type** property is used.</span></span>  
  
5.  <span data-ttu-id="b0d41-119">Sélectionnez le **nom de fichier de transmission dans l’en-tête MIME** case à cocher pour envoyer un nom de fichier dans le cadre de l’en-tête MIME du message AS2 sortant.</span><span class="sxs-lookup"><span data-stu-id="b0d41-119">Select the **Transmit file name in MIME header** check box to send a file name as part of the MIME header for the outbound AS2 message.</span></span> <span data-ttu-id="b0d41-120">Pour spécifier le nom de fichier, sélectionnez **indiquer le nom de fichier** ou **que système génère le nom de fichier**.</span><span class="sxs-lookup"><span data-stu-id="b0d41-120">To specify the file name, select **Specify file name** or **Have system generate file name**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b0d41-121">En sélectionnant **que système génère le nom de fichier** génère une nouvelle valeur GUID comme nom de fichier de chaque pièce jointe du message AS2.</span><span class="sxs-lookup"><span data-stu-id="b0d41-121">Selecting **Have system generate file name** will generate a new GUID value as the file name of each attachment sent in the AS2 message.</span></span>  
  
6.  <span data-ttu-id="b0d41-122">Si vous avez sélectionné **indiquer le nom de fichier**, entrez une propriété de contexte ou la valeur de chaîne dans le **indiquer le nom de fichier** champ.</span><span class="sxs-lookup"><span data-stu-id="b0d41-122">If you selected **Specify file name**, enter a string value or context property in the **Specify file name** field.</span></span> <span data-ttu-id="b0d41-123">Vous pouvez également activer **suspendre le message si la propriété de contexte (%propriété%)) introuvable** de suspendre le message si la propriété de contexte sélectionné n’existe pas pour le message sortant.</span><span class="sxs-lookup"><span data-stu-id="b0d41-123">You can also enable **Suspend message if context property (e.g. %property%) not found** to suspend the message if the selected context property does not exist for the outbound message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b0d41-124">Pour spécifier une propriété de contexte, placez son nom entre les caractères %.</span><span class="sxs-lookup"><span data-stu-id="b0d41-124">To specify a context-property, enclose the property name with the % character.</span></span> <span data-ttu-id="b0d41-125">Par exemple, `%FILE.ReceivedFileName%`.</span><span class="sxs-lookup"><span data-stu-id="b0d41-125">For example, `%FILE.ReceivedFileName%`.</span></span>  
  
7.  <span data-ttu-id="b0d41-126">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="b0d41-126">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0d41-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0d41-127">See Also</span></span>  
 [<span data-ttu-id="b0d41-128">Configuration des paramètres de l’hôte Local (AS2)</span><span class="sxs-lookup"><span data-stu-id="b0d41-128">Configuring Local Host Settings (AS2)</span></span>](../core/configuring-local-host-settings-as2.md)
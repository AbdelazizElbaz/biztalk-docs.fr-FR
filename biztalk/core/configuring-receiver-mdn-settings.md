---
title: "Configuration des paramètres MDN du récepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eae6431d-a2b9-4889-a29c-720e801a644e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dafe17a0ad357b840b31d8a10c67e1ae3cc1e415
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-receiver-mdn-settings"></a><span data-ttu-id="b6425-102">Configuration des paramètres MDN du récepteur</span><span class="sxs-lookup"><span data-stu-id="b6425-102">Configuring Receiver MDN Settings</span></span>
<span data-ttu-id="b6425-103">Vous pouvez spécifier les propriétés qui régissent la génération de MDN basée sur les en-têtes de message AS2 dans les paramètres MDN de réception.</span><span class="sxs-lookup"><span data-stu-id="b6425-103">As part of receiver MDN settings, you can specify the properties that govern MDN generation based on the AS2 message header.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b6425-104">Aucuns propriétés ne sont désactivées sur **tiers A -> tiers B** onglet d’accord unidirectionnel si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher pour le tiers A. Toutefois, toutes les propriétés sont désactivées sur la même page dans le **tiers B -> tiers A** onglet si vous avez sélectionné la case à cocher lors de la création du tiers A.</span><span class="sxs-lookup"><span data-stu-id="b6425-104">No properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are disabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b6425-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b6425-105">Prerequisites</span></span>  
 <span data-ttu-id="b6425-106">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b6425-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-receiver-mdn-settings"></a><span data-ttu-id="b6425-107">Configuration des paramètres MDN du récepteur</span><span class="sxs-lookup"><span data-stu-id="b6425-107">To configure receiver MDN settings</span></span>  
  
1.  <span data-ttu-id="b6425-108">Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md).</span><span class="sxs-lookup"><span data-stu-id="b6425-108">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="b6425-109">Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="b6425-109">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="b6425-110">Sous l’onglet accord unidirectionnel, sous **paramètres d’hôte Local** , cliquez sur **paramètres MDN du récepteur**.</span><span class="sxs-lookup"><span data-stu-id="b6425-110">On a one-way agreement tab, under **Local Host Settings** section, click **Receiver MDN Settings**.</span></span>  
  
3.  <span data-ttu-id="b6425-111">Si vous n’avez pas coché le **utiliser les paramètres de l’accord pour validation et MDN au lieu de l’en-tête de message** propriété dans le **Validations** page, vous pouvez choisir pour que le tiers qui envoie le MDN signe le MDN si génération du MDN est activée par le **Disposition-Notification-to** en-tête AS2, mais la **Disposition-Notification-Options** en-tête n’active pas la signature.</span><span class="sxs-lookup"><span data-stu-id="b6425-111">If you did not check the **Use agreement settings for validation and MDN instead of message header** property in the **Validations** page, you can choose to have the party sending the MDN, sign the MDN if generation of the MDN is enabled by the **Disposition-Notification-to** AS2 header, but the **Disposition-Notification-Options** header does not enable signing.</span></span> <span data-ttu-id="b6425-112">Cela peut se produire si **Disposition-Notification-Options** n’est pas définie ou est défini comme facultatif.</span><span class="sxs-lookup"><span data-stu-id="b6425-112">This can occur if **Disposition-Notification-Options** is either not set or is set to optional.</span></span> <span data-ttu-id="b6425-113">Vous pouvez le faire en cliquant sur **signer le MDN si l’en-tête Disposition-Notification-Option n’est pas prédéfinie, ou si l’en-tête Signed-Receipt-Protocol est défini comme facultatif**.</span><span class="sxs-lookup"><span data-stu-id="b6425-113">You can do so by clicking **Sign requested MDN if Disposition-Notification-Option header is not preset or if Signed-Receipt-Protocol header is set to optional**.</span></span>  
  
4.  <span data-ttu-id="b6425-114">Vous pouvez saisir du texte dans le **texte du MDN** champ pour que le tiers expéditeur du MDN l’ajoute au message MDN (dans le champ Content-Description).</span><span class="sxs-lookup"><span data-stu-id="b6425-114">You can enter a text in the **MDN Text** field to have the party sending the MDN add it to the MDN message (under the Content-Description field).</span></span> <span data-ttu-id="b6425-115">Ce paramètre est applicable que la génération du MDN ait été basée sur les en-têtes AS2 ou sur les propriétés de l'accord.</span><span class="sxs-lookup"><span data-stu-id="b6425-115">This setting is applicable irrespective of whether the MDN was generated based upon the AS2 headers or the agreement properties.</span></span>  
  
5.  <span data-ttu-id="b6425-116">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="b6425-116">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6425-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6425-117">See Also</span></span>  
 [<span data-ttu-id="b6425-118">Configuration des paramètres de l’hôte Local (AS2)</span><span class="sxs-lookup"><span data-stu-id="b6425-118">Configuring Local Host Settings (AS2)</span></span>](../core/configuring-local-host-settings-as2.md)
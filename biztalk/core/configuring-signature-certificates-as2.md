---
title: Configuration des certificats de Signature (AS2) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8539e210-1656-4fff-b026-36b81689061f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32a52962976c2db62de902906f53f5c270e2c7c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-signature-certificates-as2"></a><span data-ttu-id="960be-102">Configuration des certificats de signature (AS2)</span><span class="sxs-lookup"><span data-stu-id="960be-102">Configuring Signature Certificates (AS2)</span></span>
<span data-ttu-id="960be-103">Dans le cadre des paramètres de cette page, vous pouvez spécifier les certificats à utiliser pour signer les messages sortants et le MDN qui résout cet accord.</span><span class="sxs-lookup"><span data-stu-id="960be-103">As part of the settings on this page, you can specify the certificates to be used for signing all outgoing messages and MDN that resolve to this agreement.</span></span> <span data-ttu-id="960be-104">Les paramètres de cette page remplacent les paramètres de certificat fournis dans le cadre des propriétés du groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="960be-104">The settings on this page override the certificate settings provided as part of the BizTalk Group properties.</span></span> <span data-ttu-id="960be-105">Pour plus d’informations sur l’utilisation des certificats, consultez [configuration des certificats pour AS2](../core/configuring-certificates-for-as2.md).</span><span class="sxs-lookup"><span data-stu-id="960be-105">For more information on how certificates are used, see [Configuring Certificates for AS2](../core/configuring-certificates-for-as2.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="960be-106">Aucuns propriétés ne sont désactivées dans cette page, même si vous avez désactivé la **BizTalk Local traite les messages reçus par le tiers ou prend en charge l’envoi de messages à partir de ce tiers** case à cocher lors de la création du tiers pour lequel vous créez le accord.</span><span class="sxs-lookup"><span data-stu-id="960be-106">No properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="960be-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="960be-107">Prerequisites</span></span>  
 <span data-ttu-id="960be-108">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="960be-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-agreement-level-signature-certificate"></a><span data-ttu-id="960be-109">Pour configurer le certificat de signature au niveau de l'accord</span><span class="sxs-lookup"><span data-stu-id="960be-109">To configure agreement-level signature certificate</span></span>  
  
1.  <span data-ttu-id="960be-110">Créer un accord AS2, comme décrit dans [configuration des paramètres généraux (AS2)](../core/configuring-general-settings-as2.md).</span><span class="sxs-lookup"><span data-stu-id="960be-110">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="960be-111">Pour mettre à jour un accord AS2 existant, cliquez sur l’accord dans le **tiers et profils d’entreprise** page, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="960be-111">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="960be-112">Sous l’onglet accord unidirectionnel, cliquez sur **certificats de Signature**.</span><span class="sxs-lookup"><span data-stu-id="960be-112">On a one-way agreement tab, click **Signature Certificates**.</span></span>  
  
3.  <span data-ttu-id="960be-113">Sélectionnez le **groupe de remplacement de certificat de signature** case à cocher pour utiliser le certificat fourni dans cette page pour la signature des messages AS2 sortants et MDN.</span><span class="sxs-lookup"><span data-stu-id="960be-113">Select the **Override group signing certificate** check box to use the certificate provided in this page for signing outgoing AS2 messages and MDN.</span></span>  
  
4.  <span data-ttu-id="960be-114">Cliquez sur **Parcourir** pour afficher les **sélectionner un certificat** boîte de dialogue, dans laquelle vous sélectionnez le certificat de signature à appliquer aux messages transmis par ce tiers.</span><span class="sxs-lookup"><span data-stu-id="960be-114">Click **Browse** to display the **Select Certificate** dialog box, where you select the signature certificate to apply to messages transmitted by this party.</span></span>  
  
5.  <span data-ttu-id="960be-115">Le **nom commun** zone de texte affiche une description du certificat sélectionné.</span><span class="sxs-lookup"><span data-stu-id="960be-115">The **Common Name** text box displays a description of the selected certificate.</span></span>  
  
6.  <span data-ttu-id="960be-116">Le **l’empreinte numérique** zone de texte affiche l’empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="960be-116">The **Thumbprint** text box displays the thumbprint of certificate.</span></span> <span data-ttu-id="960be-117">Le format de l'empreinte de certificat est HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, où H est une valeur hexadécimale (nombre de 0 à 9 ou lettre de A à F).</span><span class="sxs-lookup"><span data-stu-id="960be-117">The certificate thumbprint has the format HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH, where H is a hexadecimal digit (a number from 0 through 9 or a letter from A through F).</span></span>  
  
7.  <span data-ttu-id="960be-118">Cliquez sur **supprimer le certificat** pour supprimer le certificat sélectionné.</span><span class="sxs-lookup"><span data-stu-id="960be-118">Click **Remove Certificate** to remove the selected certificate.</span></span>  
  
8.  <span data-ttu-id="960be-119">Cliquez sur **appliquer** pour accepter les modifications avant de poursuivre la configuration, ou cliquez sur **OK** pour valider les modifications, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="960be-119">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="960be-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="960be-120">See Also</span></span>  
 [<span data-ttu-id="960be-121">Configuration des propriétés d’accord AS2</span><span class="sxs-lookup"><span data-stu-id="960be-121">Configuring AS2 Agreement Properties</span></span>](../core/configuring-as2-agreement-properties.md)
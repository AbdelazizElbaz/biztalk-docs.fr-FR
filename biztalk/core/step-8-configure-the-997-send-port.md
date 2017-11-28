---
title: "Étape 8 : Configurer le Port de 997 envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4780c491-9f1a-4f13-b346-6a2e1801ec09
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec3c022ec1236d760c69250a2faecc7cacdb543c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-configure-the-997-send-port"></a><span data-ttu-id="a8d10-102">Étape 8 : Configurer le Port de 997 envoi</span><span class="sxs-lookup"><span data-stu-id="a8d10-102">Step 8: Configure the 997 Send Port</span></span>
<span data-ttu-id="a8d10-103">![Étape 8 sur 11](../core/media/tut-step8-of-11.gif "Tut_Step8_of_11")</span><span class="sxs-lookup"><span data-stu-id="a8d10-103">![Step 8 of 11](../core/media/tut-step8-of-11.gif "Tut_Step8_of_11")</span></span>  
  
 <span data-ttu-id="a8d10-104">Cette étape vous permet de configurer un port d'envoi pour envoyer le message 997 au partenaire.</span><span class="sxs-lookup"><span data-stu-id="a8d10-104">In this step, you set up a send port to send the 997 message to the partner.</span></span> <span data-ttu-id="a8d10-105">Ce port d'envoi utilise le pipeline d'envoi AS2EdiSend pour transporter un accusé de réception 997 EDIINT/AS2 vers le dossier _997ToFabrikam.</span><span class="sxs-lookup"><span data-stu-id="a8d10-105">This send port uses the AS2EdiSend send pipeline to transport an EDIINT/AS2-encoded 997 acknowledgment to the _997ToFabrikam folder.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a8d10-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a8d10-106">Prerequisites</span></span>  
 <span data-ttu-id="a8d10-107">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8d10-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-create-the-sendasync997-send-port"></a><span data-ttu-id="a8d10-108">Pour créer le port d'envoi Send_Async_997</span><span class="sxs-lookup"><span data-stu-id="a8d10-108">To create the Send_Async_997 send port</span></span>  
  
1.  <span data-ttu-id="a8d10-109">Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, sous le nœud BizTalk Application 1, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique** .</span><span class="sxs-lookup"><span data-stu-id="a8d10-109">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the BizTalk Application 1 node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a8d10-110">Vous utilisez un port d'envoi unidirectionnel statique, car aucun MDN n'a été configuré en tant que récepteur des messages AS2 au niveau du tiers Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="a8d10-110">You will use a static one-way send port because no MDN has been set up for the Fabrikam party as an AS2 message receiver.</span></span>  
  
2.  <span data-ttu-id="a8d10-111">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, nommez votre port d’envoi **Send_Async_997**.</span><span class="sxs-lookup"><span data-stu-id="a8d10-111">In the **Send Port Properties** dialog box, name your send port **Send_Async_997**.</span></span> <span data-ttu-id="a8d10-112">Sélectionnez **HTTP** pour **Type**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="a8d10-112">Select **HTTP** for **Type**, and then click **Configure**.</span></span>  
  
3.  <span data-ttu-id="a8d10-113">Dans le **propriétés du Transport HTTP** boîte de dialogue, pour **URL de Destination**, entrez `http://localhost/Fabrikam/Default.aspx?Destination=_997ToFabrikam`.</span><span class="sxs-lookup"><span data-stu-id="a8d10-113">In the **HTTP Transport Properties** dialog box, for **Destination URL**, enter `http://localhost/Fabrikam/Default.aspx?Destination=_997ToFabrikam`.</span></span> <span data-ttu-id="a8d10-114">Désactivez **activer le codage segmenté** puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a8d10-114">Clear **Enable chunked encoding** and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a8d10-115">Le **URL de Destination** paramètre s’assure que le port d’envoi envoie le message 997 vers le répertoire virtuel Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="a8d10-115">The **Destination URL** setting ensures that the send port will send the 997 message to the Fabrikam virtual directory.</span></span> <span data-ttu-id="a8d10-116">Le fichier Default.aspx.cs associé à ce répertoire virtuel permet de créer le message 997 avec une extension .msg, puis de l'envoyer dans le dossier de destination.</span><span class="sxs-lookup"><span data-stu-id="a8d10-116">The Default.aspx.cs file associated with that virtual directory builds the 997 with an .msg extension, and sends it to the destination folder.</span></span>  
  
4.  <span data-ttu-id="a8d10-117">Dans le **propriétés de Port d’envoi** boîte de dialogue, sélectionnez **AS2EdiSend** pour **Pipeline d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="a8d10-117">In the **Send Port Properties** dialog box, select **AS2EdiSend** for **Send Pipeline**.</span></span>  
  
5.  <span data-ttu-id="a8d10-118">Cliquez sur **filtres** dans l’arborescence de la console.</span><span class="sxs-lookup"><span data-stu-id="a8d10-118">Click **Filters** in the console tree.</span></span> <span data-ttu-id="a8d10-119">Pour **propriété**, sélectionnez **BTS. MessageType**.</span><span class="sxs-lookup"><span data-stu-id="a8d10-119">For **Property**, select **BTS.MessageType**.</span></span> <span data-ttu-id="a8d10-120">Pour **opérateur**, sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="a8d10-120">For **Operator**, select **==**.</span></span> <span data-ttu-id="a8d10-121">Pour **valeur**, entrez `http://schemas.microsoft.com/Edi/X12#X12_997_Root`.</span><span class="sxs-lookup"><span data-stu-id="a8d10-121">For **Value**, enter `http://schemas.microsoft.com/Edi/X12#X12_997_Root`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a8d10-122">Ce filtre garantit que le port d'envoi récupère uniquement les accusés de réception 997 dans MessageBox.</span><span class="sxs-lookup"><span data-stu-id="a8d10-122">This filter ensures that the send port will only pick up 997 acknowledgments from the MessageBox.</span></span>  
  
6.  <span data-ttu-id="a8d10-123">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a8d10-123">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="a8d10-124">Dans le **Ports d’envoi** volet de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit le **Send_Async_997** port d’envoi, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="a8d10-124">In the **Send Ports** pane of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send_Async_997** send port, and then click **Start**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a8d10-125">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a8d10-125">Next Steps</span></span>  
 <span data-ttu-id="a8d10-126">Configurer le port d’envoi (**Send_Payload_EdiXml**) pour envoyer la charge EDI à Contoso, comme décrit dans [étape 9 : configurer le Port d’envoi EDI charge utile](../core/step-9-configure-the-edi-payload-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="a8d10-126">You configure the send port (**Send_Payload_EdiXml**) to send the EDI payload to Contoso, as described in [Step 9: Configure the EDI Payload Send Port](../core/step-9-configure-the-edi-payload-send-port.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d10-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8d10-127">See Also</span></span>  
 <span data-ttu-id="a8d10-128">[Envoi des Messages AS2 par BizTalk Server](../core/how-biztalk-server-sends-as2-messages.md) </span><span class="sxs-lookup"><span data-stu-id="a8d10-128">[How BizTalk Server Sends AS2 Messages](../core/how-biztalk-server-sends-as2-messages.md) </span></span>  
 [<span data-ttu-id="a8d10-129">Configuration d’un Port d’envoi statique pour les Messages via AS2</span><span class="sxs-lookup"><span data-stu-id="a8d10-129">Configuring a Static Send Port for Messages over AS2</span></span>](../core/configuring-a-static-send-port-for-messages-over-as2.md)
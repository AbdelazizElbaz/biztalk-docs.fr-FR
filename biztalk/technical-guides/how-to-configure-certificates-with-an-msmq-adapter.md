---
title: Comment configurer des certificats avec un adaptateur MSMQ | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 922a171d-705f-4465-acda-212aa3797c57
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f36e3d13920982f79fe693a306a8123f089c76e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-certificates-with-an-msmq-adapter"></a><span data-ttu-id="700fe-102">Comment configurer des certificats avec un adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="700fe-102">How to Configure Certificates with an MSMQ Adapter</span></span>
<span data-ttu-id="700fe-103">L’adaptateur d’envoi MSMQ peut aider à sécuriser une connexion avec les serveurs qui acceptent ou demandent des certificats clients.</span><span class="sxs-lookup"><span data-stu-id="700fe-103">The MSMQ send adapter can help secure a connection with servers that accept or require client certificates.</span></span> <span data-ttu-id="700fe-104">Si un certificat client est spécifié, l’adaptateur d’envoi MSMQ utilise le certificat lors de la connexion avec les serveurs qui demandent ou acceptent des certificats clients.</span><span class="sxs-lookup"><span data-stu-id="700fe-104">If a client certificate is specified, the MSMQ send adapter uses the certificate when connecting with servers that require or accept client certificates.</span></span> <span data-ttu-id="700fe-105">Si le certificat client n’est pas spécifié et le serveur de destination requiert des certificats clients, l’expéditeur n’est pas authentifié et d’envoi MSMQ adaptateur ne parvient pas à envoyer le message et suit la logique de nouvelle tentative standard.</span><span class="sxs-lookup"><span data-stu-id="700fe-105">If the client certificate is not specified and the destination server requires client certificates, the sender is not authenticated and the MSMQ send adapter fails to send the message and follows the standard retry logic.</span></span>  
  
 <span data-ttu-id="700fe-106">MSMQ adaptateur d’envoi utilise le certificat client dans le magasin personnel du compte sous lequel le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est en cours.</span><span class="sxs-lookup"><span data-stu-id="700fe-106">The MSMQ send adapter uses the client certificate from the personal store of the account under which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process is running.</span></span> <span data-ttu-id="700fe-107">Le certificat est spécifié par son empreinte.</span><span class="sxs-lookup"><span data-stu-id="700fe-107">The certificate is specified by its thumbprint.</span></span> <span data-ttu-id="700fe-108">Si l’adaptateur d’envoi MSMQ ne parvient pas à charger le certificat pour une raison quelconque, le message envoyé est interrompu.</span><span class="sxs-lookup"><span data-stu-id="700fe-108">If the MSMQ send adapter fails to load the certificate for any reason, the message that it was sending is suspended.</span></span>  
  
 <span data-ttu-id="700fe-109">Lorsque vous utilisez un adaptateur MSMQ pour envoyer un message signé ou chiffré, configurez la propriété de transport MSMQ d’empreinte numérique du certificat pour le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="700fe-109">When using an MSMQ adapter to send an encrypted or signed message, configure the Certificate Thumbprint MSMQ transport property for the send port.</span></span> <span data-ttu-id="700fe-110">Dans cette propriété, spécifiez l’empreinte numérique du certificat à utiliser pour l’authentification des messages.</span><span class="sxs-lookup"><span data-stu-id="700fe-110">In this property, specify the thumbprint of the certificate to use for message authentication.</span></span> <span data-ttu-id="700fe-111">Utilisez cette propriété en combinaison avec la propriété Utiliser l'authentification pour vérifier les messages.</span><span class="sxs-lookup"><span data-stu-id="700fe-111">Use this property in combination with the Use Authentication property to verify the message.</span></span> <span data-ttu-id="700fe-112">Accédez aux files d'attente à l'aide des propriétés Nom d'utilisateur et Mot de passe.</span><span class="sxs-lookup"><span data-stu-id="700fe-112">Use the User Name and Password properties to gain access to queues.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="700fe-113">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="700fe-113">Prerequisites</span></span>  
 <span data-ttu-id="700fe-114">Pour exécuter la procédure dans cette rubrique, vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="700fe-114">To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-biztalk-server-to-send-messages-over-an-msmq-connection"></a><span data-ttu-id="700fe-115">Pour configurer BizTalk Server pour envoyer des messages via une connexion MSMQ</span><span class="sxs-lookup"><span data-stu-id="700fe-115">To configure BizTalk Server to send messages over an MSMQ connection</span></span>  
  
1.  <span data-ttu-id="700fe-116">Dans la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, créez un port d’envoi MSMQ ou ouvrez les propriétés de port d’envoi un MSMQ existant.</span><span class="sxs-lookup"><span data-stu-id="700fe-116">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, create a new MSMQ send port or open the properties for an existing MSMQ send port.</span></span>  
  
2.  <span data-ttu-id="700fe-117">Cliquez sur **configurer** dans les **Transport** section de la **propriétés de Port d’envoi** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="700fe-117">Click **Configure** in the **Transport** section of the **Send Port Properties** dialog box.</span></span>  
  
3.  <span data-ttu-id="700fe-118">Dans le **propriétés du Transport MSMQ** boîte de dialogue, pour **authentification**, sélectionnez **True**.</span><span class="sxs-lookup"><span data-stu-id="700fe-118">In the **MSMQ Transport Properties** dialog box, for **Authentication**, select **True**.</span></span>  
  
4.  <span data-ttu-id="700fe-119">Pour **empreinte numérique du certificat**, entrez l’empreinte numérique approprié.</span><span class="sxs-lookup"><span data-stu-id="700fe-119">For **Certificate thumbprint**, enter the appropriate thumbprint.</span></span>  
  
5.  <span data-ttu-id="700fe-120">Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="700fe-120">Click **OK**, and then click **OK** again.</span></span>
---
title: Comment configurer des certificats avec un adaptateur SOAP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20ee05c5-9cea-456d-bff6-49dd249f0ff4
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e382fa9084fd728e04efa29900fb0222d8b05ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-certificates-with-a-soap-adapter"></a><span data-ttu-id="ba82a-102">Comment configurer des certificats avec un adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="ba82a-102">How to Configure Certificates with a SOAP Adapter</span></span>
<span data-ttu-id="ba82a-103">L’adaptateur d’envoi SOAP peut aider à sécuriser une connexion avec les serveurs qui acceptent ou demandent des certificats clients.</span><span class="sxs-lookup"><span data-stu-id="ba82a-103">The SOAP send adapter can help secure a connection with servers that accept or require client certificates.</span></span> <span data-ttu-id="ba82a-104">Si un certificat client est spécifié, l'adaptateur d'envoi SOAP utilise le certificat lors de la connexion aux serveurs qui demandent ou acceptent des certificats clients.</span><span class="sxs-lookup"><span data-stu-id="ba82a-104">If you specify a client certificate, the SOAP send adapter uses the certificate when connecting with servers that require or accept client certificates.</span></span> <span data-ttu-id="ba82a-105">Si vous ne spécifiez pas un certificat client et le serveur de destination requiert des certificats clients, l’expéditeur n’est pas authentifié et l’envoi SOAP adaptateur ne parvient pas à envoyer le message et suit la logique de nouvelle tentative standard.</span><span class="sxs-lookup"><span data-stu-id="ba82a-105">If you do not specify a client certificate and the destination server requires client certificates, the sender is not authenticated and the SOAP send adapter fails to send the message and follows the standard retry logic.</span></span>  
  
 <span data-ttu-id="ba82a-106">L'adaptateur d'envoi SOAP utilise le certificat client du magasin Personnel du compte sous lequel le processus [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est exécuté.</span><span class="sxs-lookup"><span data-stu-id="ba82a-106">The SOAP send adapter uses the client certificate from the Personal store of the account under which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process is running.</span></span> <span data-ttu-id="ba82a-107">L'adaptateur SOAP spécifie le certificat par son empreinte.</span><span class="sxs-lookup"><span data-stu-id="ba82a-107">The SOAP adapter specifies the certificate by its thumbprint.</span></span> <span data-ttu-id="ba82a-108">Si l'adaptateur d'envoi SOAP ne peut pas charger le certificat pour une raison quelconque, le message envoyé est interrompu.</span><span class="sxs-lookup"><span data-stu-id="ba82a-108">If the SOAP send adapter fails to load the certificate for any reason, the message that it was sending is suspended.</span></span>  
  
 <span data-ttu-id="ba82a-109">Lorsque vous utilisez un adaptateur SOAP pour envoyer un message signé ou chiffré, configurez la propriété de transport SOAP empreinte de certificat Client pour le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="ba82a-109">When using a SOAP adapter to send an encrypted or signed message, configure the Client Certificate Thumbprint SOAP transport property for the send port.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ba82a-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="ba82a-110">Prerequisites</span></span>  
 <span data-ttu-id="ba82a-111">Pour exécuter la procédure dans cette rubrique, vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="ba82a-111">To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-biztalk-server-to-send-messages-over-a-soap-connection"></a><span data-ttu-id="ba82a-112">Pour configurer BizTalk Server pour envoyer des messages via une connexion SOAP</span><span class="sxs-lookup"><span data-stu-id="ba82a-112">To configure BizTalk Server to send messages over a SOAP connection</span></span>  
  
1.  <span data-ttu-id="ba82a-113">Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, créez un port d’envoi SOAP ou ouvrez les propriétés de port d’envoi un SOAP existante.</span><span class="sxs-lookup"><span data-stu-id="ba82a-113">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, create a new SOAP send port or open the properties for an existing SOAP send port.</span></span>  
  
2.  <span data-ttu-id="ba82a-114">Cliquez sur **configurer** dans les **Transport** section de la **propriétés de Port d’envoi** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="ba82a-114">Click **Configure** in the **Transport** section of the **Send Port Properties** dialog box.</span></span>  
  
3.  <span data-ttu-id="ba82a-115">Sur le **général** sous l’onglet **type d’authentification**, sélectionnez **anonyme**, **base**, **Digest**, ou **NTLM**.</span><span class="sxs-lookup"><span data-stu-id="ba82a-115">On the **General** tab, in **Authentication type**, select **Anonymous**, **Basic**, **Digest**, or **NTLM**.</span></span>  
  
4.  <span data-ttu-id="ba82a-116">Si le type d’authentification est **base** ou **Digest**, sélectionnez **n’utilisez pas l’authentification unique sur** (auquel cas vous devez spécifier le nom d’utilisateur et un mot de passe) ou sélectionnez  **Utiliser l’authentification unique sur** (auquel cas vous devez sélectionner l’Application associée).</span><span class="sxs-lookup"><span data-stu-id="ba82a-116">If the authentication type is **Basic** or **Digest**, either select **Do not use Single Sign-On** (in which case you must specify the user name and password) or select **Use Single Sign-On** (in which case you must select the Affiliate Application).</span></span>  
  
5.  <span data-ttu-id="ba82a-117">Dans **l’empreinte numérique du certificat SSL client**, entrez l’empreinte numérique approprié.</span><span class="sxs-lookup"><span data-stu-id="ba82a-117">In **SSL client certificate thumbprint**, enter the appropriate thumbprint.</span></span>  
  
6.  <span data-ttu-id="ba82a-118">Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="ba82a-118">Click **OK**, and then click **OK** again.</span></span>
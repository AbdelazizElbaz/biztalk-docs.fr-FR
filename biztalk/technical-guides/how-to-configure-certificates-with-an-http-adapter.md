---
title: Comment configurer des certificats avec un adaptateur HTTP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc2f454f-22b5-4113-9a23-e00a816d5e48
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f74b0a88983ede90899dac908a5407f8406ec1e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-certificates-with-an-http-adapter"></a><span data-ttu-id="d22aa-102">Comment configurer des certificats avec un adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="d22aa-102">How to Configure Certificates with an HTTP Adapter</span></span>
<span data-ttu-id="d22aa-103">L’adaptateur d’envoi HTTP peut aider à sécuriser une connexion avec les serveurs qui acceptent ou demandent des certificats clients.</span><span class="sxs-lookup"><span data-stu-id="d22aa-103">The HTTP send adapter can help secure a connection with servers that accept or require client certificates.</span></span> <span data-ttu-id="d22aa-104">Si un certificat client est spécifié, l'adaptateur d'envoi HTTP utilise le certificat lors de la connexion aux serveurs qui demandent ou acceptent des certificats clients.</span><span class="sxs-lookup"><span data-stu-id="d22aa-104">If a client certificate is specified, the HTTP send adapter uses the certificate when connecting with servers that require or accept client certificates.</span></span> <span data-ttu-id="d22aa-105">Si le certificat client n’est pas spécifié et que le serveur de destination requiert des certificats clients, l’expéditeur n’est pas authentifié et le protocole HTTP d’envoi échoue d’adaptateur pour envoyer le message et suit la logique de nouvelle tentative standard.</span><span class="sxs-lookup"><span data-stu-id="d22aa-105">If the client certificate is not specified and the destination server requires client certificates, the sender is not authenticated and the HTTP send adapter fails to send the message and follows the standard retry logic.</span></span>  
  
 <span data-ttu-id="d22aa-106">L'adaptateur d'envoi HTTP utilise le certificat client du magasin Personnel du compte sous lequel le processus [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est exécuté.</span><span class="sxs-lookup"><span data-stu-id="d22aa-106">The HTTP send adapter uses the client certificate from the personal store of the account under which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process is running.</span></span> <span data-ttu-id="d22aa-107">Le certificat est spécifié par son empreinte.</span><span class="sxs-lookup"><span data-stu-id="d22aa-107">The certificate is specified by its thumbprint.</span></span> <span data-ttu-id="d22aa-108">Si l'adaptateur d'envoi HTTP ne peut pas charger le certificat pour une raison quelconque, le message envoyé est interrompu.</span><span class="sxs-lookup"><span data-stu-id="d22aa-108">If the HTTP send adapter fails to load the certificate for any reason, the message that it was sending is suspended.</span></span>  
  
 <span data-ttu-id="d22aa-109">Lorsque vous utilisez un adaptateur HTTP pour envoyer un message signé ou chiffré, configurez l’empreinte de certificat SSL propriété de transport HTTP pour le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="d22aa-109">When using an HTTP adapter to send an encrypted or signed message, configure the SSL certificate thumbprint HTTP transport property for the send port.</span></span> <span data-ttu-id="d22aa-110">Dans cette propriété, spécifiez l’empreinte numérique du certificat à utiliser pour l’authentification des messages.</span><span class="sxs-lookup"><span data-stu-id="d22aa-110">In this property, specify the thumbprint of the certificate to use for message authentication.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d22aa-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d22aa-111">Prerequisites</span></span>  
 <span data-ttu-id="d22aa-112">Pour exécuter la procédure dans cette rubrique, vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="d22aa-112">To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-biztalk-server-to-send-messages-over-an-http-connection"></a><span data-ttu-id="d22aa-113">Pour configurer BizTalk Server pour envoyer des messages via une connexion HTTP</span><span class="sxs-lookup"><span data-stu-id="d22aa-113">To configure BizTalk Server to send messages over an HTTP connection</span></span>  
  
1.  <span data-ttu-id="d22aa-114">Dans la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, créez un port d’envoi HTTP ou ouvrez les propriétés de port d’envoi HTTP existant.</span><span class="sxs-lookup"><span data-stu-id="d22aa-114">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, create a new HTTP send port or open the properties for an existing HTTP send port.</span></span>  
  
2.  <span data-ttu-id="d22aa-115">Cliquez sur **configurer** dans la section de Transport de la **propriétés de Port d’envoi** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="d22aa-115">Click **Configure** in the Transport section of the **Send Port Properties** dialog box.</span></span>  
  
3.  <span data-ttu-id="d22aa-116">Cliquez sur **authentification** dans les **propriétés du Transport HTTP** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="d22aa-116">Click **Authentication** in the **HTTP Transport Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="d22aa-117">Dans **type d’authentification**, sélectionnez **anonyme**, **base**, **Digest**, ou **Kerberos**.</span><span class="sxs-lookup"><span data-stu-id="d22aa-117">In **Authentication type**, select **Anonymous**, **Basic**, **Digest**, or **Kerberos**.</span></span>  
  
5.  <span data-ttu-id="d22aa-118">Si le type d’authentification est **base** ou **Digest**, sélectionnez **n’utilisez pas l’authentification unique sur** (auquel cas vous devez spécifier le nom d’utilisateur et un mot de passe) ou sélectionnez  **Utiliser l’authentification unique sur** (auquel cas vous devez sélectionner l’Application associée).</span><span class="sxs-lookup"><span data-stu-id="d22aa-118">If the authentication type is **Basic** or **Digest**, either select **Do not use Single Sign-On** (in which case you must specify the user name and password) or select **Use Single Sign-On** (in which case you must select the Affiliate Application).</span></span>  
  
6.  <span data-ttu-id="d22aa-119">Dans **l’empreinte numérique du certificat SSL client**, entrez l’empreinte numérique approprié.</span><span class="sxs-lookup"><span data-stu-id="d22aa-119">In **SSL client certificate thumbprint**, enter the appropriate thumbprint.</span></span>  
  
7.  <span data-ttu-id="d22aa-120">Cliquez sur **OK**, puis cliquez sur **OK** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="d22aa-120">Click **OK**, and then click **OK** again.</span></span>
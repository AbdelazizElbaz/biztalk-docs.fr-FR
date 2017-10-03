---
title: "Recommandations de sécurité de l’adaptateur SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [SMTP adapters], security
- SMTP adapters, security
- security, SMTP adapters
ms.assetid: 45f13744-a0eb-4b4e-85cd-6b862b384ad5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca1aeed0ad8c80cc32d333aeef37d1da6feabfc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="smtp-adapter-security-recommendations"></a><span data-ttu-id="22b3c-102">Recommandations de sécurité de l’adaptateur SMTP</span><span class="sxs-lookup"><span data-stu-id="22b3c-102">SMTP Adapter Security Recommendations</span></span>
<span data-ttu-id="22b3c-103">L'adaptateur SMTP permet d'échanger des informations entre un serveur exécutant BizTalk Server et d'autres applications via le protocole SMTP (Simple Mail Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="22b3c-103">You use the SMTP adapter to exchange information between a server running BizTalk Server and other applications by means of the Simple Mail Transfer Protocol (SMTP) protocol.</span></span> <span data-ttu-id="22b3c-104">BizTalk Server peut envoyer des messages à d'autres applications en créant un message électronique qu'il remet à une adresse de messagerie spécifiée.</span><span class="sxs-lookup"><span data-stu-id="22b3c-104">BizTalk Server can send messages to other applications by creating an e-mail message and delivering it to a specified e-mail address.</span></span> <span data-ttu-id="22b3c-105">L'adaptateur SMTP sert uniquement à l'envoi des messages.</span><span class="sxs-lookup"><span data-stu-id="22b3c-105">You can use the SMTP adapter only for sending messages.</span></span> <span data-ttu-id="22b3c-106">Pour plus d’informations sur l’adaptateur SMTP, consultez [adaptateur SMTP](../core/smtp-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="22b3c-106">For more information about the SMTP adapter, see [SMTP Adapter](../core/smtp-adapter.md).</span></span>  
  
 <span data-ttu-id="22b3c-107">Lorsque vous configurez le compte de service pour l'instance d'hôte qui exécute l'adaptateur SMTP, vous devez spécifier le type d'authentification que vous souhaitez utiliser avec le serveur SMTP distant.</span><span class="sxs-lookup"><span data-stu-id="22b3c-107">When you configure the service account for the host instance running the SMTP adapter, you need to specify the type of authentication you want to use with the remote SMTP server.</span></span> <span data-ttu-id="22b3c-108">Les options d'authentification suivantes sont disponibles : Authentification de base (texte clair), NTLM (à l'aide des informations d'identifications actuelles) et Aucune (si l'authentification n'est pas requise par le serveur SMTP).</span><span class="sxs-lookup"><span data-stu-id="22b3c-108">The authentication options are basic authentication (clear text), NTLM (by using current credentials), or none if authentication is not required by the SMTP server.</span></span>  
  
 <span data-ttu-id="22b3c-109">Lorsque vous envoyez un message à l'aide de l'adaptateur SMTP, BizTalk Server envoie le message en texte clair par défaut.</span><span class="sxs-lookup"><span data-stu-id="22b3c-109">When you send a message by using the SMTP adapter, BizTalk Server sends the message in clear text by default.</span></span> <span data-ttu-id="22b3c-110">Si vous utilisez un pipeline doté d'un composant de codage S/MIME, vous pouvez chiffrer le message avant de l'envoyer au serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="22b3c-110">If you use a pipeline that has an S/MIME encoder component, you can encrypt the message before you send it to the SMTP server.</span></span> <span data-ttu-id="22b3c-111">Toutefois, l'en-tête SMTP est toujours en texte clair.</span><span class="sxs-lookup"><span data-stu-id="22b3c-111">However, the SMTP header is still in clear text.</span></span>  
  
 <span data-ttu-id="22b3c-112">Si vous souhaitez auditer les messages électroniques envoyés par BizTalk Server, vous devez utiliser l'adaptateur SMTP pour le connecter à votre propre serveur SMTP, sur lequel vous pouvez ensuite auditer les messages.</span><span class="sxs-lookup"><span data-stu-id="22b3c-112">If you want to audit the e-mail messages that BizTalk Server sends, you should use the SMTP adapter to connect to your own SMTP server, where you can then audit the messages.</span></span>  
  
 <span data-ttu-id="22b3c-113">L'adaptateur SMTP ne prend pas en charge le protocole SSL (Secure Sockets Layer).</span><span class="sxs-lookup"><span data-stu-id="22b3c-113">The SMTP adapter does not support Secure Sockets Layer (SSL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22b3c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22b3c-114">See Also</span></span>  
 <span data-ttu-id="22b3c-115">[Ports pour les serveurs de l’envoi et la réception](../core/ports-for-the-receive-and-send-servers.md) </span><span class="sxs-lookup"><span data-stu-id="22b3c-115">[Ports for the Receive and Send Servers](../core/ports-for-the-receive-and-send-servers.md) </span></span>  
 [<span data-ttu-id="22b3c-116">Droits d’utilisateur de sécurité minimales</span><span class="sxs-lookup"><span data-stu-id="22b3c-116">Minimum Security User Rights</span></span>](../core/minimum-security-user-rights.md)
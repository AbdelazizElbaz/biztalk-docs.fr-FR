---
title: "Comment supprimer un certificat à partir d’un Port d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, certificates
- managing [send ports], certificates
- certificates, deleting
- deleting, certificates
ms.assetid: fd93a83f-c2aa-4de2-9996-4ca4ec6d4a4c
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5193b1b6003660aac0e0b427da0f0a338b56d8ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-a-certificate-from-a-send-port"></a><span data-ttu-id="097db-102">Suppression d'un certificat d'un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="097db-102">How to Remove a Certificate from a Send Port</span></span>
<span data-ttu-id="097db-103">Cette rubrique décrit comment supprimer un certificat de sécurité d'un port d'envoi à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="097db-103">This topic describes how to use the BizTalk Server Administration console to remove a security certificate from a send port.</span></span> <span data-ttu-id="097db-104">Une fois cette opération effectuée, le port d'envoi ne chiffrera plus les messages. Ils seront désormais envoyés en texte clair.</span><span class="sxs-lookup"><span data-stu-id="097db-104">When you do this, the send port will no longer encrypt messages; messages will be sent in clear text.</span></span> <span data-ttu-id="097db-105">Supprimer un certificat d'un port d'envoi ne le supprime pas automatiquement du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="097db-105">Removing a certificate from a send port does not remove it from the certificate store.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="097db-106">Le développeur peut supprimer un certificat de sécurité d'un port d'envoi au cours du processus de développement à l'aide de la procédure décrite dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="097db-106">The application developer can remove a security certificate from a send port during the development process by using the procedure in this topic.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="097db-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="097db-107">Prerequisites</span></span>  
 <span data-ttu-id="097db-108">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="097db-108">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="097db-109">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="097db-109">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-remove-a-certificate-from-a-send-port"></a><span data-ttu-id="097db-110">Pour supprimer un certificat d'un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="097db-110">To remove a certificate from a send port</span></span>  
  
1.  <span data-ttu-id="097db-111">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="097db-111">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="097db-112">Dans l'arborescence de la console, développez le groupe BizTalk, puis l'application BizTalk dont dépend le port d'envoi dans lequel supprimer un certificat.</span><span class="sxs-lookup"><span data-stu-id="097db-112">In the console tree, expand the BizTalk group and the BizTalk application for which you want to remove a certificate from a send port.</span></span>  
  
3.  <span data-ttu-id="097db-113">Développez **Ports d’envoi**, cliquez sur le port d’envoi, cliquez sur **propriétés**, puis cliquez sur **certificats**.</span><span class="sxs-lookup"><span data-stu-id="097db-113">Expand **Send Ports**, right-click the send port, click **Properties**, and then click **Certificates**.</span></span>  
  
4.  <span data-ttu-id="097db-114">Cliquez sur **supprimer le certificat**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="097db-114">Click **Remove certificate**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="097db-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="097db-115">See Also</span></span>  
 [<span data-ttu-id="097db-116">Création et configuration des Ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="097db-116">Creating and Configuring Send Ports</span></span>](../core/creating-and-configuring-send-ports.md)
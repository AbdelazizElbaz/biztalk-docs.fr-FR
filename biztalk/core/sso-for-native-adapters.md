---
title: "L’authentification unique pour les adaptateurs natifs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, SSO
- SSO, adapters
ms.assetid: d8527f0f-910c-42ce-9bd3-83ab6d4349c0
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45aaf357d943853cc9504762437f554f1d28efb7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-for-native-adapters"></a><span data-ttu-id="7008f-102">SSO pour adaptateurs natifs</span><span class="sxs-lookup"><span data-stu-id="7008f-102">SSO for Native Adapters</span></span>
<span data-ttu-id="7008f-103">L'authentification unique de l'entreprise (SSO) vous permet de ne vous authentifier qu'une seule fois auprès de différents systèmes informatiques ou sites web.</span><span class="sxs-lookup"><span data-stu-id="7008f-103">Enterprise Single Sign-On (SSO) enables you to sign on only once when interoperating with different computer systems or Web sites.</span></span> <span data-ttu-id="7008f-104">Ce composant de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet aux adaptateurs BizTalk de fournir le bon identifiant d'utilisateur et les bonnes informations d'identification à de multiples applications utilisant, au sein de votre réseau, un mécanisme d'authentification commun basé sur vos informations d'identification Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="7008f-104">This feature of Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables BizTalk adapters to provide the appropriate user ID and credentials to multiple applications within your network that use a common authentication mechanism based on your Microsoft Windows credentials.</span></span> <span data-ttu-id="7008f-105">Une fois que Windows a authentifié vos informations d'identification, vous n'avez plus besoin de fournir d'autres informations d'identification pour vous connecter aux applications.</span><span class="sxs-lookup"><span data-stu-id="7008f-105">After Windows authenticates your credentials, you do not need to provide additional credentials to connect to the applications.</span></span>  
  
 <span data-ttu-id="7008f-106">La SSO est disponible pour les adaptateurs HTTP et SOAP, bien qu'elle soit désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="7008f-106">SSO is available for the HTTP and SOAP adapters, although it is disabled by default.</span></span> <span data-ttu-id="7008f-107">Pour l'adaptateur HTTP, vous pouvez configurer le port d'envoi et l'emplacement de réception pour utiliser la SSO ; pour l'adaptateur SOAP, vous ne pouvez configurer que l'emplacement de réception pour utiliser la SSO.</span><span class="sxs-lookup"><span data-stu-id="7008f-107">For the HTTP adapter, you can configure the send port and receive location to use SSO; for the SOAP adapter, you can configure only the receive location to use SSO.</span></span> <span data-ttu-id="7008f-108">Pour les deux adaptateurs, vous utilisez la console d'administration de Biz Talk Server pour configurer la SSO.</span><span class="sxs-lookup"><span data-stu-id="7008f-108">For both adapters, you use the BizTalk Server Administration console to configure SSO.</span></span>  
  
 <span data-ttu-id="7008f-109">L'authentification pour la SSO repose en premier lieu sur l'authentification Windows et sur les groupes Windows créés dans Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7008f-109">Authentication in SSO relies primarily on Windows authentication and the Windows groups created in Active Directory.</span></span> <span data-ttu-id="7008f-110">Toutes les opérations effectuées par un utilisateur ou un administrateur avec la SSO nécessitent l'authentification préalable de l'utilisateur ou de l'administrateur par Windows.</span><span class="sxs-lookup"><span data-stu-id="7008f-110">All operations completed by a user or administrator with SSO require that Windows authenticate the user or administrator first.</span></span>  
  
 <span data-ttu-id="7008f-111">Pour plus d'informations sur le fonctionnement de la SSO avec les adaptateurs HTTP et SOAP, consultez les rubriques adéquates dans Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="7008f-111">For more information about how SSO works with the HTTP and SOAP adapters, see the appropriate topics in See Also.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7008f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7008f-112">See Also</span></span>  
 <span data-ttu-id="7008f-113">[À l’aide de l’authentification unique](../core/using-sso.md) </span><span class="sxs-lookup"><span data-stu-id="7008f-113">[Using SSO](../core/using-sso.md) </span></span>  
 <span data-ttu-id="7008f-114">[Adaptateur HTTP](../core/http-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="7008f-114">[HTTP Adapter](../core/http-adapter.md) </span></span>  
 [<span data-ttu-id="7008f-115">Adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="7008f-115">SOAP Adapter</span></span>](../core/soap-adapter.md)
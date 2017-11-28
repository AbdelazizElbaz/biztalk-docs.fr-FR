---
title: "Prise en charge de l’authentification unique pour les adaptateurs d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45dc2597-0036-4444-8b35-d18621b003d8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d590ada6b8ee80c942714a698d0001c207ac6751
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-support-for-send-adapters"></a><span data-ttu-id="bf106-102">Prise en charge de l'authentification unique pour les adaptateurs d'envoi</span><span class="sxs-lookup"><span data-stu-id="bf106-102">SSO Support for Send Adapters</span></span>
<span data-ttu-id="bf106-103">L'authentification unique (SSO) de l'entreprise inclut des services permettant de stocker et de transmettre, sous forme chiffrée, des informations d'identification de l'utilisateur au niveau local et réseau, y compris au niveau des domaines.</span><span class="sxs-lookup"><span data-stu-id="bf106-103">Enterprise Single Sign-On (SSO) provides services to store and transmit encrypted user credentials across local, network, and domain boundaries.</span></span> <span data-ttu-id="bf106-104">Lors de la création d'un adaptateur de transport, vous pouvez gérer les informations d'identification utilisateur dont aura besoin l'adaptateur de transport pour accéder aux applications principales à l'aide des API SSO.</span><span class="sxs-lookup"><span data-stu-id="bf106-104">When you create a transport adapter, you can leverage SSO APIs to handle the user credentials that a transport adapter uses to access back-end applications.</span></span>  
  
 <span data-ttu-id="bf106-105">Les adaptateurs de transport qui ne prennent pas en charge l'authentification unique doivent généralement être configurés avec un seul jeu d'informations d'identification afin d'accéder aux applications principales.</span><span class="sxs-lookup"><span data-stu-id="bf106-105">Transport adapters that do not support SSO are usually required to be configured with a single set of credentials that they use for accessing back-end applications.</span></span> <span data-ttu-id="bf106-106">Pour la plupart de ces systèmes principaux cependant, l'authentification par compte unique peut ne pas répondre à toutes leurs exigences de sécurité.</span><span class="sxs-lookup"><span data-stu-id="bf106-106">For many back-end systems, single account authentication may not satisfy all security enforcements.</span></span> <span data-ttu-id="bf106-107">De nombreuses applications fournissent des droits d'accès différents en fonction de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bf106-107">Many applications provide different access rights depending on the user who is accessing them.</span></span> <span data-ttu-id="bf106-108">Avec l'authentification unique, les adaptateurs peuvent choisir de manière dynamique les informations d'identification à utiliser pour le point de terminaison, en fonction de l'utilisateur qui tente d'y accéder.</span><span class="sxs-lookup"><span data-stu-id="bf106-108">SSO allows adapters to dynamically choose the credentials to use for the endpoint based on the user who is trying to access it.</span></span>  
  
## <a name="how-send-adapters-work-with-sso"></a><span data-ttu-id="bf106-109">Fonctionnement des adaptateurs d'envoi avec l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="bf106-109">How Send Adapters Work with SSO</span></span>  
 <span data-ttu-id="bf106-110">Envoyer des adaptateurs qui prennent en charge l’authentification unique valident et échanger le ticket et d’obtenir les informations d’identification de l’utilisateur à partir du système d’authentification unique à l’aide de la **ISSOTicket.ValidateAndRedeemTicket** API.</span><span class="sxs-lookup"><span data-stu-id="bf106-110">Send adapters that support SSO validate and redeem the ticket and obtain the user credentials from the SSO system by using the **ISSOTicket.ValidateAndRedeemTicket** API.</span></span> <span data-ttu-id="bf106-111">Ils se servent ensuite des informations d'identification ainsi obtenues pour l'authentification avec le point de terminaison de destination.</span><span class="sxs-lookup"><span data-stu-id="bf106-111">The adapter uses the obtained credentials to authenticate with the destination endpoint.</span></span>  
  
 <span data-ttu-id="bf106-112">Le fragment de code suivant montre comment un adaptateur d'envoi récupère les informations d'identification  utilisateur à partir du système d'authentification unique :</span><span class="sxs-lookup"><span data-stu-id="bf106-112">The following code fragment demonstrates how a send adapter obtains the user credentials from the SSO system:</span></span>  
  
```  
public class MyAdapter : IBTTransport,   
                         IBTTransportConfig,   
                         IBTTransportControl,  
                        IPersistPropertyBag,   
                         IBaseComponent  
{  
...  
     private string m_UserName = null;  
     private string m_UserPassword = null;  
  
 // Get user credentials from SSO  
 // AffiliateAppVal is the name of SSO affiliate   
 // application for the specific destination endpoint  
     private void GetUserCredentials(  
 IBaseMessage message,   
 string AffiliateAppVal )  
     {  
 string creds[] = null;  
 string externalUserName = null;  
  
 ISSOTicket ssoTicket = new ISSOTicket();  
 creds = ssoTicket.ValidateAndRedeemTicket(  
 message,   
 AffiliateAppVal,   
 0,   
 out externalUserName);  
  
 m_UserName = externalUserName;  
 m_UserPassword = creds[0];  
     }  
...  
}  
```  
  
## <a name="party-resolution"></a><span data-ttu-id="bf106-113">Résolution du tiers</span><span class="sxs-lookup"><span data-stu-id="bf106-113">Party Resolution</span></span>  
 <span data-ttu-id="bf106-114">Le composant de pipeline Résolution du tiers est chargé pour mapper le certificat ou l’identificateur de sécurité (SID) de l’expéditeur au tiers de BizTalk Server configuré correspondant.</span><span class="sxs-lookup"><span data-stu-id="bf106-114">The Party Resolution pipeline component is responsible for mapping the sender certificate or the sender security identifier (SID) to the corresponding configured BizTalk Server party.</span></span> <span data-ttu-id="bf106-115">Cartes dotées de ces informations à leur disposition doivent définir le message deux système propriétés de contexte, **WindowsUser** et **SignatureCertificate**, pour être consommé par la résolution du tiers en aval composant si configuré.</span><span class="sxs-lookup"><span data-stu-id="bf106-115">Adapters that have this information available to them should set the two system message context properties, **WindowsUser** and **SignatureCertificate**, to be consumed by the downstream party resolution component if configured.</span></span>  
  
 <span data-ttu-id="bf106-116">Le **WindowsUser** propriété est remplie avec l’utilisateur de domaine de l’expéditeur, par exemple redmond\myBtsUser.</span><span class="sxs-lookup"><span data-stu-id="bf106-116">The **WindowsUser** property is populated with the domain user of the sender, for example redmond\myBtsUser.</span></span> <span data-ttu-id="bf106-117">Le **SignatureCertificate** propriété est remplie avec l’empreinte numérique du certificat d’authentification client.</span><span class="sxs-lookup"><span data-stu-id="bf106-117">The **SignatureCertificate** property is populated with the thumbprint of the client authentication certificate.</span></span>  
  
## <a name="managing-passwords"></a><span data-ttu-id="bf106-118">La gestion des mots de passe</span><span class="sxs-lookup"><span data-stu-id="bf106-118">Managing passwords</span></span>  
 <span data-ttu-id="bf106-119">Si vous placez directement les informations d'identification dans les propriétés d'un point de terminaison, la valeur du champ de mot de passe est effacée lors de l'exportation d'un fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="bf106-119">If you put credentials directly in the properties of an endpoint, the password field will be blanked out when you need to export a binding file.</span></span> <span data-ttu-id="bf106-120">Vous devrez disposer des droits d'administrateur pour entrer de nouveau le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="bf106-120">This will require your user to re-enter the password as an administrator.</span></span> <span data-ttu-id="bf106-121">Pour éviter ce problème, utilisez l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="bf106-121">You can avoid this difficulty by using SSO for credentials.</span></span>
---
title: "Prise en charge de l’authentification unique pour les adaptateurs de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4767387c-f24b-4986-aaed-6724c5d6b347
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e3c992f47ad46b4a9d5ee095ad650f6cc492179
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-support-for-receive-adapters"></a><span data-ttu-id="433df-102">Prise en charge de l'authentification unique pour les adaptateurs de réception</span><span class="sxs-lookup"><span data-stu-id="433df-102">SSO Support for Receive Adapters</span></span>
<span data-ttu-id="433df-103">L'authentification unique (SSO) de l'entreprise inclut des services permettant de stocker et de transmettre, sous forme chiffrée, des informations d'identification de l'utilisateur au niveau local et réseau, y compris au niveau des domaines.</span><span class="sxs-lookup"><span data-stu-id="433df-103">Enterprise Single Sign-On (SSO) provides services to store and transmit encrypted user credentials across local, network, and domain boundaries.</span></span> <span data-ttu-id="433df-104">Enregistreurs d’adaptateur de transport peuvent tirer parti des API de l’authentification unique pour gérer les informations d’identification utilisateur à un adaptateur de transport utilise pour accéder aux applications principales.</span><span class="sxs-lookup"><span data-stu-id="433df-104">Transport adapter writers can leverage SSO APIs to handle the user credentials that a transport adapter uses to access back-end applications.</span></span>  
  
 <span data-ttu-id="433df-105">Les adaptateurs de transport qui ne prennent pas en charge l'authentification unique doivent généralement être configurés avec un seul jeu d'informations d'identification afin d'accéder aux applications principales.</span><span class="sxs-lookup"><span data-stu-id="433df-105">Transport adapters that do not support SSO are usually required to be configured with a single set of credentials that they use for accessing back-end applications.</span></span> <span data-ttu-id="433df-106">Pour la plupart de ces systèmes principaux cependant, l'authentification par compte unique peut ne pas répondre à toutes leurs exigences de sécurité.</span><span class="sxs-lookup"><span data-stu-id="433df-106">For many back-end systems, single account authentication may not satisfy all security enforcements.</span></span> <span data-ttu-id="433df-107">De nombreuses applications fournissent des droits d'accès différents en fonction de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="433df-107">Many applications provide different access rights depending on the user who is accessing them.</span></span> <span data-ttu-id="433df-108">Avec l'authentification unique, les adaptateurs peuvent choisir de manière dynamique les informations d'identification à utiliser pour le point de terminaison, en fonction de l'utilisateur qui tente d'y accéder.</span><span class="sxs-lookup"><span data-stu-id="433df-108">SSO allows adapters to dynamically choose the credentials to use for the endpoint based on the user who is trying to access it.</span></span>  
  
## <a name="how-receive-adapters-work-with-sso"></a><span data-ttu-id="433df-109">Fonctionnement des adaptateurs de réception avec l'authentification unique</span><span class="sxs-lookup"><span data-stu-id="433df-109">How Receive Adapters Work with SSO</span></span>  
 <span data-ttu-id="433df-110">Les adaptateurs de réception qui prennent en charge l'authentification unique effectuent les étapes suivantes après la réception d'un message et avant sa publication dans BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="433df-110">Receive adapters that support SSO perform the following steps after receiving a message and before publishing it to BizTalk Server:</span></span>  
  
1.  <span data-ttu-id="433df-111">L’adaptateur emprunte l’identité de l’expéditeur et obtient le ticket d’authentification unique pour le compte de l’expéditeur à l’aide de la **ISSOTicket.IssueTicket** API.</span><span class="sxs-lookup"><span data-stu-id="433df-111">The adapter impersonates the sender and obtains the SSO ticket on behalf of the sender by using the **ISSOTicket.IssueTicket** API.</span></span>  
  
2.  <span data-ttu-id="433df-112">L'adaptateur stocke le ticket SSO ainsi récupéré dans la propriété de contexte de message « SSOTicket » sous l'espace de noms système.</span><span class="sxs-lookup"><span data-stu-id="433df-112">After successfully obtaining an SSO ticket the adapter stores it on the message context property “SSOTicket” under the system namespace.</span></span>  
  
 <span data-ttu-id="433df-113">Le fragment de code suivant montre l'obtention du ticket et son stockage dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="433df-113">The following code fragment demonstrates how the ticket is obtained and how it is stored on the message context.</span></span>  
  
```  
public class MyAdapter : IBTTransport,   
                         IBTTransportConfig,   
                         IBTTransportControl,  
                         IPersistPropertyBag,   
                         IBaseComponent  
{  
...  
     private string m_SSOToken = null;  
  
 // Get a ticket for the sender  
     private void GetSSOTicket(IntPtr token)  
     {  
       bool impersonated = false;  
      WindowsImpersonationContext wic = null;  
  
 if (token != (IntPtr)0)   
 {  
     try   
 {  
         // Impersonate the user using his security  
 // token  
            WindowsIdentity wi =   
 new WindowsIdentity(token);  
            wic = wi.Impersonate();  
            impersonated = true;  
  
         // Get an SSO ticket for the impersonated  
 // user  
            ISSOTicket ssoTicket = new ISSOTicket();  
            m_SSOToken = ssoTicket.IssueTicket(0);  
         }  
         finally   
 {  
           if (impersonated)  
            // Revert the impersonation  
            wic.Undo();  
          }  
}  
}  
...  
  
     private void WriteSSOTicketToContext(  
 IBaseMessage message )  
     {  
         if (m_SSOTicket != null)   
 {  
 // Write the SSO ticket to the message context  
          message.Context.Write(  
 “SSOTicket”,  
 http://schemas.microsoft.com/BizTalk/2003/system-properties,   
 m_SSOToken);  
        }  
      }  
}  
```  
  
## <a name="party-resolution"></a><span data-ttu-id="433df-114">Résolution du tiers</span><span class="sxs-lookup"><span data-stu-id="433df-114">Party Resolution</span></span>  
 <span data-ttu-id="433df-115">Le composant de pipeline Résolution du tiers est chargé pour mapper le certificat ou l’identificateur de sécurité (SID) de l’expéditeur au tiers de BizTalk Server configuré correspondant.</span><span class="sxs-lookup"><span data-stu-id="433df-115">The Party Resolution pipeline component is responsible for mapping the sender certificate or the sender security identifier (SID) to the corresponding configured BizTalk Server party.</span></span> <span data-ttu-id="433df-116">Cartes dotées de ces informations à leur disposition doivent définir le message deux système propriétés de contexte, **WindowsUser** et **SignatureCertificate**, pour être consommé par la résolution du tiers en aval composant si configuré.</span><span class="sxs-lookup"><span data-stu-id="433df-116">Adapters that have this information available to them should set the two system message context properties, **WindowsUser** and **SignatureCertificate**, to be consumed by the downstream party resolution component if configured.</span></span>  
  
 <span data-ttu-id="433df-117">Le **WindowsUser** propriété est remplie avec l’utilisateur de domaine de l’expéditeur, par exemple redmond\myBtsUser.</span><span class="sxs-lookup"><span data-stu-id="433df-117">The **WindowsUser** property is populated with the domain user of the sender, for example redmond\myBtsUser.</span></span> <span data-ttu-id="433df-118">Le **SignatureCertificate** propriété est remplie avec l’empreinte numérique du certificat d’authentification client.</span><span class="sxs-lookup"><span data-stu-id="433df-118">The **SignatureCertificate** property is populated with the thumbprint of the client authentication certificate.</span></span>  
  
## <a name="managing-passwords"></a><span data-ttu-id="433df-119">Gestion des mots de passe</span><span class="sxs-lookup"><span data-stu-id="433df-119">Managing Passwords</span></span>  
 <span data-ttu-id="433df-120">Si vous placez directement les informations d'identification dans les propriétés d'un point de terminaison, la valeur du champ de mot de passe est effacée lors de l'exportation d'un fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="433df-120">If you put credentials directly in the properties of an endpoint, the password field will be blanked out when you need to export a binding file.</span></span> <span data-ttu-id="433df-121">Vous devrez disposer des droits d'administrateur pour entrer de nouveau le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="433df-121">This will require your user to re-enter the password as an administrator.</span></span> <span data-ttu-id="433df-122">Pour éviter ce problème, utilisez l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="433df-122">You can avoid this difficulty by using SSO for credentials.</span></span>  
  
 <span data-ttu-id="433df-123">Si le point de terminaison de l’adaptateur a un **mot de passe** propriété, sachez que la valeur réelle est stockée en texte clair dans la base de données de configuration SSO.</span><span class="sxs-lookup"><span data-stu-id="433df-123">If the adapter endpoint has a **Password** property, be aware that the actual value is stored in clear text in the SSO Configure Store database.</span></span> <span data-ttu-id="433df-124">et ce même si elle s'affiche dans l'interface utilisateur sous la forme d'astérisques (« * »).</span><span class="sxs-lookup"><span data-stu-id="433df-124">This is despite the fact that it is displayed in the user interface as "*".</span></span> <span data-ttu-id="433df-125">Cette propriété est également transmise via le réseau et peut être lue par un simple script à l'aide de l'exemple BizTalk Server ExplorerOM.</span><span class="sxs-lookup"><span data-stu-id="433df-125">This property is also transferred through the network and a simple script using the BizTalk Server sample ExplorerOM will be able to read it.</span></span>
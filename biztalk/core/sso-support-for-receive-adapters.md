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
# <a name="sso-support-for-receive-adapters"></a>Prise en charge de l'authentification unique pour les adaptateurs de réception
L'authentification unique (SSO) de l'entreprise inclut des services permettant de stocker et de transmettre, sous forme chiffrée, des informations d'identification de l'utilisateur au niveau local et réseau, y compris au niveau des domaines. Enregistreurs d’adaptateur de transport peuvent tirer parti des API de l’authentification unique pour gérer les informations d’identification utilisateur à un adaptateur de transport utilise pour accéder aux applications principales.  
  
 Les adaptateurs de transport qui ne prennent pas en charge l'authentification unique doivent généralement être configurés avec un seul jeu d'informations d'identification afin d'accéder aux applications principales. Pour la plupart de ces systèmes principaux cependant, l'authentification par compte unique peut ne pas répondre à toutes leurs exigences de sécurité. De nombreuses applications fournissent des droits d'accès différents en fonction de l'utilisateur. Avec l'authentification unique, les adaptateurs peuvent choisir de manière dynamique les informations d'identification à utiliser pour le point de terminaison, en fonction de l'utilisateur qui tente d'y accéder.  
  
## <a name="how-receive-adapters-work-with-sso"></a>Fonctionnement des adaptateurs de réception avec l'authentification unique  
 Les adaptateurs de réception qui prennent en charge l'authentification unique effectuent les étapes suivantes après la réception d'un message et avant sa publication dans BizTalk Server :  
  
1.  L’adaptateur emprunte l’identité de l’expéditeur et obtient le ticket d’authentification unique pour le compte de l’expéditeur à l’aide de la **ISSOTicket.IssueTicket** API.  
  
2.  L'adaptateur stocke le ticket SSO ainsi récupéré dans la propriété de contexte de message « SSOTicket » sous l'espace de noms système.  
  
 Le fragment de code suivant montre l'obtention du ticket et son stockage dans le contexte du message.  
  
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
  
## <a name="party-resolution"></a>Résolution du tiers  
 Le composant de pipeline Résolution du tiers est chargé pour mapper le certificat ou l’identificateur de sécurité (SID) de l’expéditeur au tiers de BizTalk Server configuré correspondant. Cartes dotées de ces informations à leur disposition doivent définir le message deux système propriétés de contexte, **WindowsUser** et **SignatureCertificate**, pour être consommé par la résolution du tiers en aval composant si configuré.  
  
 Le **WindowsUser** propriété est remplie avec l’utilisateur de domaine de l’expéditeur, par exemple redmond\myBtsUser. Le **SignatureCertificate** propriété est remplie avec l’empreinte numérique du certificat d’authentification client.  
  
## <a name="managing-passwords"></a>Gestion des mots de passe  
 Si vous placez directement les informations d'identification dans les propriétés d'un point de terminaison, la valeur du champ de mot de passe est effacée lors de l'exportation d'un fichier de liaison. Vous devrez disposer des droits d'administrateur pour entrer de nouveau le mot de passe. Pour éviter ce problème, utilisez l'authentification unique.  
  
 Si le point de terminaison de l’adaptateur a un **mot de passe** propriété, sachez que la valeur réelle est stockée en texte clair dans la base de données de configuration SSO. et ce même si elle s'affiche dans l'interface utilisateur sous la forme d'astérisques (« * »). Cette propriété est également transmise via le réseau et peut être lue par un simple script à l'aide de l'exemple BizTalk Server ExplorerOM.
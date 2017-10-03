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
# <a name="sso-support-for-send-adapters"></a>Prise en charge de l'authentification unique pour les adaptateurs d'envoi
L'authentification unique (SSO) de l'entreprise inclut des services permettant de stocker et de transmettre, sous forme chiffrée, des informations d'identification de l'utilisateur au niveau local et réseau, y compris au niveau des domaines. Lors de la création d'un adaptateur de transport, vous pouvez gérer les informations d'identification utilisateur dont aura besoin l'adaptateur de transport pour accéder aux applications principales à l'aide des API SSO.  
  
 Les adaptateurs de transport qui ne prennent pas en charge l'authentification unique doivent généralement être configurés avec un seul jeu d'informations d'identification afin d'accéder aux applications principales. Pour la plupart de ces systèmes principaux cependant, l'authentification par compte unique peut ne pas répondre à toutes leurs exigences de sécurité. De nombreuses applications fournissent des droits d'accès différents en fonction de l'utilisateur. Avec l'authentification unique, les adaptateurs peuvent choisir de manière dynamique les informations d'identification à utiliser pour le point de terminaison, en fonction de l'utilisateur qui tente d'y accéder.  
  
## <a name="how-send-adapters-work-with-sso"></a>Fonctionnement des adaptateurs d'envoi avec l'authentification unique  
 Envoyer des adaptateurs qui prennent en charge l’authentification unique valident et échanger le ticket et d’obtenir les informations d’identification de l’utilisateur à partir du système d’authentification unique à l’aide de la **ISSOTicket.ValidateAndRedeemTicket** API. Ils se servent ensuite des informations d'identification ainsi obtenues pour l'authentification avec le point de terminaison de destination.  
  
 Le fragment de code suivant montre comment un adaptateur d'envoi récupère les informations d'identification  utilisateur à partir du système d'authentification unique :  
  
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
  
## <a name="party-resolution"></a>Résolution du tiers  
 Le composant de pipeline Résolution du tiers est chargé pour mapper le certificat ou l’identificateur de sécurité (SID) de l’expéditeur au tiers de BizTalk Server configuré correspondant. Cartes dotées de ces informations à leur disposition doivent définir le message deux système propriétés de contexte, **WindowsUser** et **SignatureCertificate**, pour être consommé par la résolution du tiers en aval composant si configuré.  
  
 Le **WindowsUser** propriété est remplie avec l’utilisateur de domaine de l’expéditeur, par exemple redmond\myBtsUser. Le **SignatureCertificate** propriété est remplie avec l’empreinte numérique du certificat d’authentification client.  
  
## <a name="managing-passwords"></a>La gestion des mots de passe  
 Si vous placez directement les informations d'identification dans les propriétés d'un point de terminaison, la valeur du champ de mot de passe est effacée lors de l'exportation d'un fichier de liaison. Vous devrez disposer des droits d'administrateur pour entrer de nouveau le mot de passe. Pour éviter ce problème, utilisez l'authentification unique.
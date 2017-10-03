---
title: Single Sign-prise en charge pour les adaptateurs WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF adapters, Single Sign-On
- Single Sign-On, WCF adapters
ms.assetid: 70a33d87-50bd-41de-9084-68dd66b0dbf9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 712aa01190762d6c6f74604a5f48c19fe42531d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-support-for-the-wcf-adapters"></a>Prise en charge de l'authentification unique pour les adaptateurs WCF
Vous pouvez configurer l'utilisation de l'authentification unique de l'entreprise (SSO) pour un emplacement de réception ou un port d'envoi WCF à l'aide de la console Administration de BizTalk. Cette rubrique décrit le fonctionnement de l'authentification unique avec les adaptateurs WCF.  
  
 En général, les environnements d'entreprise (au sein desquels les utilisateurs interagissent avec divers systèmes et applications) ne maintiennent pas le contexte de l'utilisateur au travers des divers processus, produits et ordinateurs. Ce contexte utilisateur est essentiel à la fourniture de fonctionnalités de l’authentification uniques, car il est nécessaire de vérifier qui a initié la demande d’origine. Pour remédier à ce problème, l'authentification unique de l'entreprise (SSO) génère un ticket SSO (différent d'un ticket Kerberos) que les applications peuvent utiliser pour obtenir les informations d'identification correspondant à l'utilisateur ayant initié la demande d'origine.  
  
 Lorsqu'un adaptateur de réception reçoit un message, il peut demander un ticket SSO auprès d'un serveur SSO. Ce ticket chiffré contient l'identité [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] de l'utilisateur à l'origine de la demande, ainsi qu'un délai d'expiration. Une fois le ticket acquis, il est ajouté en tant que propriété au message entrant. Lors de la transmission d'un message, l'adaptateur d'envoi contacte un serveur SSO avec le ticket SSO émis et le nom de l'application associée pour laquelle l'adaptateur tente de récupérer des informations d'identification. Le serveur SSO recherche les informations d'identification pour l'application associée cible, puis renvoie celles-ci à l'adaptateur d'envoi qui les utilise pour envoyer un message correctement authentifié à l'application associée.  
  
## <a name="single-sign-on-support-for-the-wcf-receive-locations"></a>Prise en charge de l'authentification unique pour les emplacements de réception WCF  
 Les paramètres de sécurité appliqués et le type de l'adaptateur WCF utilisé pour un emplacement de réception déterminent la possibilité pour un adaptateur de réception WCF d'émettre des tickets SSO. Pour que l'adaptateur de réception WCF émette un ticket SSO, les clients WCF doivent envoyer des informations d'identification que l'adaptateur peut emprunter. L'emprunt d'identité représente la capacité d'une application serveur à utiliser l'identité du client. Les informations d'identification doivent correspondre à un compte d'utilisateur [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] valide pour que l'emprunt d'identité soit correct.  
  
> [!NOTE]
>  Pour les paramètres de sécurité et les adaptateurs WCF n'exigeant pas l'envoi d'informations d'identification par les clients pour un emprunt d'identité, vous pouvez émettre des tickets SSO avec le type d'informations d'identification envoyé par les clients dans un composant de pipeline de réception personnalisé. Pour plus d’informations sur la gestion des tickets SSO dans les composants de pipeline de réception, consultez l’exemple composant de pipeline InPipelineComp, inclus dans [inventaire des fichiers de la Solution orientée services](../core/file-inventory-for-the-service-oriented-solution.md).  
  
 **Emplacement de réception unique authentification prise en charge de WCF-BasicHttp**  
  
 L'adaptateur de réception WCF-BasicHttp peut émettre un ticket d'authentification unique à partir du serveur SSO uniquement dans les configurations de sécurité présentées dans le tableau suivant.  
  
> [!NOTE]
>  Pour plus d’informations sur le mappage d’un certificat à un [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] utilisateur compte, consultez « Mappage de certificats aux comptes d’utilisateur » à [http://go.microsoft.com/fwlink/?LinkId=87478](http://go.microsoft.com/fwlink/?LinkId=87478).  
  
|Mode de sécurité|Type d'informations d'identification du client du transport|Nom d'utilisateur|  
|-------------------|--------------------------------------|------------------------------------|  
|Transport|Basic|Néant|  
|Transport|Digest|Néant|  
|Transport|Ntlm|Néant|  
|Transport|Windows|Néant|  
|Transport|Certificat|Néant|  
|Message|Néant|UserName|  
|Message|Néant|Certificat|  
|TransportWithMessageCredential|Néant|Certificat|  
|TransportWithMessageCredential|Néant|UserName|  
|TransportCredentialOnly|Basic|Néant|  
|TransportCredentialOnly|Digest|Néant|  
|TransportCredentialOnly|Ntlm|Néant|  
|TransportCredentialOnly|Windows|Néant|  
|TransportCredentialOnly|Certificat|Néant|  
  
 **Emplacement de réception unique authentification prise en charge de WCF-WSHttp**  
  
 L'adaptateur de réception WCF-WSHttp peut émettre un ticket d'authentification unique à partir du serveur SSO uniquement dans les configurations de sécurité présentées dans le tableau suivant.  
  
|Mode de sécurité|Type d'informations d'identification du client du transport|Nom d'utilisateur|  
|-------------------|--------------------------------------|------------------------------------|  
|Transport|Basic|Néant|  
|Transport|Digest|Néant|  
|Transport|Ntlm|Néant|  
|Transport|Windows|Néant|  
|Transport|Certificat|Néant|  
|Message|Néant|UserName|  
|Message|Néant|Windows|  
|Message|Néant|Certificat|  
|TransportWithMessageCredential|Néant|Windows|  
|TransportWithMessageCredential|Néant|Certificat|  
|TransportWithMessageCredential|Néant|UserName|  
  
 **Emplacement de réception unique authentification prise en charge de WCF-NetTcp**  
  
 L'adaptateur de réception WCF-NetTcp peut émettre un ticket d'authentification unique à partir du serveur SSO uniquement dans les configurations de sécurité présentées dans le tableau suivant.  
  
|Mode de sécurité|Type d'informations d'identification du client du transport|Nom d'utilisateur|  
|-------------------|--------------------------------------|------------------------------------|  
|Transport|Windows|Néant|  
|Transport|Certificat|Néant|  
|Message|Néant|Certificat|  
|Message|Néant|Windows|  
|Message|Néant|UserName|  
|TransportWithMessageCredential|Néant|Certificat|  
|TransportWithMessageCredential|Néant|Windows|  
|TransportWithMessageCredential|Néant|UserName|  
  
 S**unique authentification prise en charge pour l’emplacement de réception WCF-NetNamedPipe**  
  
 L'adaptateur de réception WCF-NetNamedPipe peut émettre un ticket SSO à partir du serveur SSO uniquement dans les configurations de sécurité présentées dans le tableau suivant.  
  
|Mode de sécurité|Type d'informations d'identification du client du transport|Nom d'utilisateur|  
|-------------------|--------------------------------------|------------------------------------|  
|Transport|Néant|Néant|  
  
 **Emplacement de réception unique authentification prise en charge de WCF-Custom et WCF-CustomIsolated**  
  
 Pour que les emplacements de réception WCF-Custom et WCF-CustomIsolated émettent des tickets SSO, les paramètres de sécurité utilisés dans les emplacements de réception requièrent l'envoi par les clients WCF d'informations d'identification susceptibles d'être empruntées par Windows Communication Foundation. WCF prend en charge l'emprunt d'identité pour différents types d'informations d'identification de client. Pour plus d’informations sur les types d’informations d’identification que WCF prend en charge l’emprunt d’identité, consultez « Délégation et emprunt d’identité avec WCF » à [http://go.microsoft.com/fwlink/?LinkId=87476](http://go.microsoft.com/fwlink/?LinkId=87476).  
  
## <a name="single-sign-on-support-for-the-wcf-send-ports"></a>Prise en charge de l'authentification unique pour les ports d'envoi WCF  
 Pour les ports d'envoi WCF, vous pouvez spécifier un nom d'application associée à utiliser pour l'authentification unique uniquement dans les configurations de sécurité présentées dans le tableau suivant.  
  
|Mode de sécurité|Type d'informations d'identification du client du transport|Nom d'utilisateur|  
|-------------------|--------------------------------------|------------------------------------|  
|Transport|Digest|Néant|  
|Transport|Basic|Néant|  
|Message|Néant|UserName|  
  
> [!NOTE]
>  Pour un service WCF port d’envoi pour valider et échanger un ticket SSO correctement, le **SSOTicket** et **OriginatorSID** propriétés de contexte doivent être disponibles dans un message à envoyer. Un emplacement de réception avec l'option d'authentification unique activée peut promouvoir ces propriétés depuis le compte [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] de l'expéditeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Enterprise Single Sign-On](../core/enterprise-single-sign-on2.md)
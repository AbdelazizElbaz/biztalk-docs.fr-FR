---
title: "Single Sign-prise en charge de l’adaptateur SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, SOAP adapters
- SOAP adapters, SharePoint Portal Server
- SOAP adapters, SSO
- SharePoint Portal server
ms.assetid: c7bf755c-c37d-4b19-9817-a7f42e1e9656
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b6e604eaf7e1b0a9b6144dc20f8bdd59d03932f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-support-for-the-soap-adapter"></a>Authentification prise en charge unique de l’adaptateur SOAP
Vous pouvez utiliser la console Administration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour configurer l'utilisation de l'authentification unique de l'entreprise (SSO) pour un emplacement de réception ou un port d'envoi SOAP. Cette rubrique décrit le fonctionnement de SSO avec l'adaptateur SOAP.  
  
 **Emplacements de réception unique authentification prise en charge de SOAP**  
  
 Les emplacements de réception SOAP prennent en charge deux versions de SSO—[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Enterprise SSO et Microsoft SharePoint Portal Server SSO. Exécutez l'Assistant Publication de services Web BizTalk pour activer le support de SharePoint Portal Server SSO. Pour plus d’informations sur l’activation de l’authentification unique de SharePoint Portal Server, consultez [publication de Services Web](../core/publishing-web-services.md). Activez l'utilisation de l'authentification unique de l'entreprise à l'aide des pages de propriétés de l'emplacement de réception SOAP. Pour plus d’informations sur l’activation de l’authentification unique de l’entreprise pour l’emplacement de réception SOAP, consultez [comment configurer un emplacement de réception SOAP](../core/how-to-configure-a-soap-receive-location.md).  
  
 **Prise en charge d’Enterprise SSO pour SOAP des emplacements de réception**  
  
 Les services Internet (IIS) reçoivent une demande SOAP d'un client Web, IIS authentifie l'utilisateur et transmet l'ID de sécurité à l'adaptateur SOAP. Si la méthode d'authentification IIS est Authentification Digest, Authentification de base ou Authentification Windows intégrée, l'adaptateur SOAP contacte le magasin d'informations d'identification SSO pour obtenir un ticket chiffré basé sur l'utilisateur authentifié. Ce ticket est stocké en tant que le **SSOTicket** propriété dans la propriété de contexte du message.  
  
 Dans le scénario de transfert, le moteur de messagerie BizTalk dirige le message vers la base de données MessageBox. Lorsqu'un adaptateur d'envoi reçoit le message de la base de données MessageBox, il appelle la méthode RedeemTicket avec le ticket chiffré, conjointement avec le nom de l'application, pour récupérer les informations de sécurité de l'application du magasin SSO. L'adaptateur d'envoi utilise alors les informations d'identification externes pour se connecter à l'application et traiter la demande. Pour plus d’informations sur les applications associées, consultez [Applications associées SSO](../core/sso-affiliate-applications.md).  
  
 Dans les cas où une orchestration appelle l'adaptateur d'envoi, le moteur de messagerie BizTalk envoie le message à la base de données MessageBox. L’orchestration doit s’assurer à la fois le **SSOTicket** propriété de contexte et le **Microsoft.BizTalk.XLANGs.BTXEngine.OriginatorSID** sont de la propriété de contexte du message qui contient le ticket conservée. Lorsque l'adaptateur reçoit ce message de la base de données MessageBox, il appelle la méthode RedeemTicket avec le ticket chiffré pour extraire les informations d'identification principales du magasin SSO. L'utilisateur concevant l'orchestration doit copier spécifiquement cette propriété dans le message.  
  
 **Prise en charge de SharePoint Portal Server SSO pour SOAP des emplacements de réception**  
  
 Lors de l'intégration avec SharePoint Portal Server, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne prend en charge l'authentification unique Microsoft SharePoint Portal Server que via l'adaptateur SOAP. SharePoint Portal Server crée des tickets SSO qu'il envoie à BizTalk Server dans un en-tête SOAP de la demande SOAP. Lorsque l’adaptateur SOAP reçoit une demande contenant un ticket d’authentification unique, le ticket est stocké en tant que le **SSOTicket** propriété dans la propriété de contexte du message. La même propriété contient un ticket d'authentification unique de l'entreprise. Un seul ticket d'authentification unique de l'entreprise peut être associé à un message BizTalk.  
  
 Dans les scénarios de transfert et d'orchestration, la gestion d'un ticket d'authentification unique émis par SharePoint Portal Server est identique à celui qui aurait été créé par l'adaptateur SOAP à l'aide de l'authentification unique de l'entreprise. Lorsqu’un adaptateur d’envoi reçoit un message, il appelle la **RedeemTicket** méthode avec le texte chiffré de ticket par SharePoint Portal Server généré. L'adaptateur d'envoi n'a pas besoin de savoir que différents tickets d'authentification unique de l'entreprise existent. Le **RedeemTicket** méthode déterminer quel système d’authentification unique généré le ticket et échangez-le depuis l’emplacement approprié.  
  
 **Utilisation combinée de Enterprise SSO de l’authentification unique et de SharePoint Portal Server**  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend en charge l'utilisation simultanée des deux systèmes d'authentification unique. L'API peut distinguer les tickets générés par chaque authentification unique et les échanger depuis la base de données de l'authentification. Si vous utilisez les deux systèmes d’authentification unique en même temps, les règles suivantes déterminent quel ticket d’authentification unique de réception SOAP promeut d’emplacement pour le **SSOTicket** propriété de contexte :  
  
-   Si aucune authentification unique n'est activée, ne promouvez pas de ticket.  
  
-   Si l'authentification unique de l'entreprise est activée, mais l'authentification unique SharePoint Portal Server ne l'est pas, récupérez et promouvez le ticket d'authentification unique de l'entreprise.  
  
-   Si l'authentification unique SharePoint Portal Server est activée, mais l'authentification unique de l'entreprise ne l'est pas, promouvez le ticket d'authentification unique SharePoint Portal Server existant.  
  
-   Si les authentifications uniques de l'entreprise et SharePoint Portal Server sont activées :  
  
    -   Si le ticket d'authentification SharePoint Portal Server est reçu, promouvez ce ticket.  
  
    -   Si le ticket d'authentification unique SharePoint Portal Server n'a pas été reçu, récupérez et promouvez le ticket d'authentification unique de l'entreprise.  
  
 **Seule l’authentification prise en charge de l’adaptateur d’envoi SOAP**  
  
 Si l’authentification unique est activée, lorsqu’un port d’envoi SOAP reçoit un message avec le **Secure** propriété (**SSOTicket**), il appelle le serveur SSO pour valider et échanger le ticket pour une application associée. L'application d'administration, les administrateurs d'applications associées ou les administrateurs SSO de l'application associée peuvent appeler SSO pour échanger un ticket. SSO déchiffre alors le ticket et obtient les informations d'identification principales. Les scénarios de transfert et d’orchestration sont les mêmes pour le port d’envoi SOAP, comme décrit dans la section « Enterprise SSO prise en charge pour les emplacements de réception SOAP » de la rubrique [unique authentification prise en charge de l’adaptateur SOAP](../core/single-sign-on-support-for-the-soap-adapter.md).  
  
 Par défaut, le port d'envoi SOAP n'active pas l'authentification unique. Pour plus d’informations sur l’activation de l’authentification unique pour le port d’envoi SOAP, consultez [comment configurer un Port d’envoi SOAP](../core/how-to-configure-a-soap-send-port.md).
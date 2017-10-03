---
title: "Configuration d’IIS pour WCF isolé des adaptateurs de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive adapters, WCF services
- WCF services, receive adapters
- IIS, configuring [WCF receive adapters]
ms.assetid: 1c6f1561-a7ba-4eb0-8878-bf213ebcd6a6
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1515a69ab6a9150668db4f3415f0483dd1ce4e7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-iis-for-the-isolated-wcf-receive-adapters"></a>Configuration d'IIS pour les adaptateurs de réception WCF isolés
Pour publier des services WCF à l'aide de l'Assistant Publication de services WCF BizTalk, vous devez configurer les services Internet (IIS), les hôtes isolés de BizTalk et les comptes du groupe Utilisateurs Windows. Cette section traite des problèmes de configuration des services Internet (IIS) pour publier les services WCF à l'aide des adaptateurs de réception WCF isolés, tels que l'adaptateur de réception WCF-BasicHttp, l'adaptateur de réception WCF-WSHttp et l'adaptateur WCF-CustomIsolated. Pour obtenir des informations générales sur l’hébergement de services WCF dans IIS, consultez « Hosting in IIS » à [http://go.microsoft.com/fwlink/?LinkId=75700](http://go.microsoft.com/fwlink/?LinkId=75700).  
  
## <a name="considerations-when-configuring-iis"></a>Considérations à prendre en compte lors de la configuration des services Internet (IIS)  
 **Internet Information Services 7.0 et 7.5**  
  
 Vous pouvez utiliser IIS 7.0 and 7.5 configurés avec ASP.NET 4.0 pour publier les services WCF à l'aide des adaptateurs de réception WCF isolés.  
  
 IIS 7.0 (pour Windows Server 2008 SP2) et IIS 7.5 (pour Windows Server 2008 R2) utilisent les pools d'applications IIS pour traiter les demandes de service Web. IIS 7.0 prend en charge plusieurs pools d'applications. Chaque processus de pool d'applications peut être exécuté sous un contexte de l'utilisateur différent.  
  
 **Hôtes BizTalk isolé**  
  
 Pour héberger les services WCF à l'aide des adaptateurs de réception WCF isolés, vous devez créer au moins un hôte isolé dans BizTalk Server. Pour plus d’informations sur la configuration des hôtes BizTalk isolé, consultez « Hôtes BizTalk isolés » dans [activation des Services Web](../core/enabling-web-services.md).  
  
 **Accès aux données de plusieurs installations de serveur**  
  
 Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et la base de données de gestion BizTalk résident sur des serveurs différents, vous devez modifier le contexte de l'utilisateur du pool d'applications IIS en un compte d'utilisateur de domaine.  
  
 Lors de l'implémentation d'un déploiement multiserveur, les groupes Windows Hôte isolé doivent exister sur le domaine auquel appartiennent les serveurs de bases de données BizTalk.  
  
 **Réduction des droits d’utilisateur et des privilèges de compte**  
  
 Utilisez des hôtes isolés pour donner aux adaptateurs, qui sont exécutés dans des processus externes, l'accès au nombre minimal de ressources requises pour interagir avec BizTalk Server. Pour un déploiement sécurisé, vous devez donner les privilèges minimaux au contexte de l'utilisateur pour les processus externes.  
  
 **Recommandations de sécurité pour l’Assistant de publication des Services Web BizTalk**  
  
 Le répertoire virtuel créé par l'Assistant Publication de services WCF BizTalk hérite des listes de contrôle d'accès (ACL) du répertoire virtuel parent ou du site Web.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication des Services WCF](../core/publishing-wcf-services.md)
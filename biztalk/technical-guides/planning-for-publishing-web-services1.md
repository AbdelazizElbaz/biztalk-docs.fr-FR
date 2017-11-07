---
title: Planification des Services web de publication | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b571c3aa-874b-43f7-af2e-5a71113a93dd
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c34539704a0725a96464fae03226fb88cdd6660c
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="planning-for-publishing-web-services"></a>Planification de la publication de Services Web
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Fournit la prise en charge intégrée pour les services Web. Il vous permet de réutiliser et d’agréger vos services Web existants dans vos orchestrations.  

## <a name="overview"></a>Vue d'ensemble
 Vous pouvez également publier (exposer) vos orchestrations en tant que services Web pour séparer le Web service logique du processus d’entreprise, ce qui vous permet de mettre à jour ou remplacer la logique métier en fonction des besoins sans toucher au code utilisé pour la logique du service Web. Cette fonctionnalité est appelée mise en œuvre de « code modulaire ». En général, il est considéré comme une meilleure pratique pour implémenter le code modulaire lorsque cela est possible. Publication de services Web requiert que vous activez les services Web et publier une orchestration ou un schéma comme un service Web à l’aide de l’Assistant de publication des Services Web BizTalk.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]prend en charge pour les adaptateurs natifs dans les services Web via l’utilisation de l’adaptateur SOAP. Une telle prise en charge offre une évolutivité, une tolérance aux pannes et des capacités de suivi pour vos services sans que vous ayez besoin d'écrire du code. Pour plus d’informations sur l’adaptateur SOAP, consultez [adaptateur SOAP](../core/soap-adapter.md).  
  
Planification des services Web peut être divisé en deux catégories, la planification de la publication de services Web et de planification pour la consommation de services Web. Cette rubrique décrit les étapes à suivre pour la publication de services Web.  
  
## <a name="enabling-web-services"></a>Activation des services web  
 Pour publier des services Web, vous devez configurer les services Internet (IIS), les hôtes BizTalk isolés et les comptes d'utilisateur et de groupe Windows. Cette section fournit une vue d’ensemble sur l’activation des services web. Pour plus d'informations sur l'activation des services Web, consultez la documentation IIS.  
  
### <a name="internet-information-services"></a>Services Internet (IIS)
 Vous pouvez publier des services Web pour les systèmes Windows IIS est configuré avec ASP.NET. Dans IIS, les tous les services Web s’exécutent dans le processus de travail ASP.NET.  
  
 IIS utilise des pools d’applications pour le traitement des demandes de service Web. IIS prend en charge plusieurs pools d’applications, et chaque processus de pool d’applications peuvent s’exécuter sous un contexte utilisateur différent.  
  
### <a name="biztalk-isolated-hosts"></a>Hôtes BizTalk isolés  
 Pour activer les services Web, vous devez créer au moins un hôte isolé dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les hôtes isolés représentent des processus externes, tels que les extensions ISAPI et les processus ASP.NET que BizTalk Server ne pas créer ou contrôler. Ces types de processus externes doivent héberger certains adaptateurs, tels que HTTP/S et SOAP.  
  
 Le Gestionnaire de Configuration de BizTalk Server crée BizTalkServerIsolatedHost que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise en tant que l’hôte isolé par défaut. Le groupe Utilisateurs d'hôtes BizTalk isolés est le nom du groupe Windows associé à cet hôte par défaut. Pour plus d’informations sur les hôtes et les instances d’hôte, consultez [gestion d’hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md).  
  
 Une instance d'hôte isolé ne peut exécuter qu'un seul adaptateur. Si vous configurez les gestionnaires de réception des adaptateurs HTTP et SOAP, avec le seul hôte isolé, vous devez créer deux pools d'applications, soit un pool d'applications par adaptateur.  
  
 Par exemple, si vous projetez de configurer deux hôtes isolés, comme suit :  
  
|Nom d’hôte isolé|Emplacements de réception|  
|------------------------|-----------------------|  
|Hôte isolé 1|HTTP_ReceiveLocation1A<br /><br /> HTTP_ReceiveLocation1B<br /><br /> SOAP_ReceiveLocation1 **Remarque :** le **hôte isolé 1** est utilisé pour les gestionnaires de réception des adaptateurs SOAP et HTTP.|  
|Hôte isolé 2|HTTP_ReceiveLocation2|  
  
 Vous pouvez créer quatre répertoires virtuels, une pour chaque emplacement de réception, comme suit :  
  
|Emplacement de réception|Répertoire virtuel|  
|----------------------|-----------------------|  
|HTTP_ReceiveLocation1A|IIS_Virtual_Directory1A|  
|HTTP_ReceiveLocation1B|IIS_Virtual_Directory1B|  
|SOAP_ReceiveLocation1|IIS_Virtual_Directory1C|  
|HTTP_ReceiveLocation2|IIS_Virtual_Directory2|  
  
 Ensuite, vous devez créer au moins trois pools d’applications pour les répertoires virtuels comme suit :  
  
> [!NOTE]  
>  Vous devez créer au moins un pool d'applications par hôte isolé.  
  
|Répertoires virtuels|Pool d'applications| Description|  
|-------------------------|----------------------|-----------------|  
|IIS_Virtual_Directory1A<br /><br /> IIS_Virtual_Directory1B|AppPool_Host1_HTTP|Un pool d'applications distinct n'est pas requis car tous les emplacements de réception ont le même hôte isolé (Hôte isolé 1) et le même protocole.|  
|IIS_Virtual_Directory1C|AppPool_Host1_SOAP|Un pool d'applications distinct est requis car l'emplacement de réception utilise un protocole différent (SOAP) des autres emplacements de réception dans le même hôte (Hôte isolé 1).|  
|IIS_Virtual_Directory2|AppPool_Host2_HTTP|Un pool d'applications distinct est requis car l'emplacement de réception s'exécute sous un hôte différent de Hôte isolé 1.|  
  
 Gardez à l’esprit les points importants suivants lorsque vous créez vos pools d’applications :  
  
-   Vous devez ajouter le compte d'utilisateur pour les pools d'applications aux groupes locaux ou de domaine appropriés des hôtes isolés. Consultez [groupe Windows et les comptes d’utilisateur dans BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
-   Vous devez faire correspondre le compte d’utilisateur entre une instance d’hôte isolé et le pool d’applications correspondant selon les tableaux précédents. Pour plus d’informations sur la relation entre les comptes d’utilisateur des pools d’instance et d’application hôte isolé, consultez [comment modifier les comptes de Service et les mots de passe](../core/how-to-change-service-accounts-and-passwords.md).  
  
### <a name="database-access-for-single-server-installations"></a>Accès de base de données pour les Installations de serveur unique  
 Si BizTalk Server et la base de données de gestion BizTalk résident sur le même serveur, vous devez définir le contexte utilisateur du processus de travail ASP.NET ou le Pool d’applications IIS pour le compte d’utilisateur ASPNET local ou à un compte d’utilisateur local ou de domaine qui dispose des privilèges minimaux.  
  
### <a name="database-access-for-multiple-server-installations"></a>Accès aux données de plusieurs Installations de serveur  
 Si BizTalk Server et la base de données de gestion BizTalk résident sur des serveurs différents, vous devez modifier le contexte de l’utilisateur du processus de travail ASP.NET ou le Pool d’applications IIS à un compte d’utilisateur de domaine.  
  
 Lors de l’implémentation d’un déploiement à plusieurs serveurs, les groupes Windows hôte isolé doivent exister sur le domaine auquel appartiennent les serveurs de base de données BizTalk.  
  
### <a name="minimizing-account-privileges-and-user-rights"></a>Réduction des droits d’utilisateur et des privilèges de compte  
 Utilisez des hôtes isolés pour donner aux adaptateurs, qui sont exécutés dans des processus externes, l'accès au nombre minimal de ressources requises pour interagir avec BizTalk Server. Pour un déploiement plus sécurisé, vous devez donner le contexte de l’utilisateur pour les processus externes des privilèges minimaux.  
  
### <a name="security-recommendations-for-biztalk-web-services-publishing-wizard"></a>Recommandations de sécurité pour l’Assistant Publication de Services Web BizTalk  
 Le répertoire virtuel créé par l'Assistant Publication de services Web BizTalk hérite des listes de contrôle d'accès (ACL) et des exigences d'authentification du répertoire virtuel parent ou du site Web. Si le répertoire virtuel parent ou le site Web autorise l'accès anonyme, l'Assistant Publication de services Web BizTalk supprime cette fonction lors de la création du répertoire virtuel.  
  
### <a name="enabling-aspnet-40-for-published-web-services"></a>Activation d’ASP.NET 4.0 pour les Services Web publiés  
Consultez [comment activer ASP.NET 4.0 pour les Services Web publiés](../core/how-to-enable-asp-net-4-0-for-published-web-services.md).  
  
## <a name="using-the-biztalk-web-services-publishing-wizard"></a>À l’aide de l’Assistant Publication de Services Web BizTalk  
 Pour plus d’informations sur la publication d’une orchestration en tant qu’un service Web, consultez [publier une Orchestration en tant que Service Web](../core/publishing-an-orchestration-as-a-web-service.md).  
  
 Pour plus d’informations sur la publication de schémas comme un service Web, consultez [publication de schémas comme un Service Web](../core/publishing-schemas-as-a-web-service.md).  
  
## <a name="planning-for-publishing-wcf-services"></a>Planification de la publication de Services WCF  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]introduit la prise en charge intégrée de Windows Communication Foundation (WCF). [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous permet de réutiliser et d'agréger vos services WCF existants dans vos orchestrations. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]implémente également la prise en charge pour les adaptateurs natifs dans les services WCF. Une telle prise en charge offre une évolutivité, une tolérance aux pannes et des capacités de suivi pour vos services WCF sans que vous ayez besoin d'écrire un code. Pour plus d’informations sur les adaptateurs WCF, consultez [adaptateurs WCF](../core/wcf-adapters.md).  
  
 Pour plus d’informations sur la planification des Services WCF dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [publication des Services WCF](../core/publishing-wcf-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Planification de la consommation de services web](../technical-guides/planning-for-consuming-web-services.md)

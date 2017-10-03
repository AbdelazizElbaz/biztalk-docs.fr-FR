---
title: Activation des Services Web | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, publishing
- hosts, isolated
- Web services, planning
- Web services, enabling
ms.assetid: 2a4681f6-9ded-423d-baa5-5831e6a85c61
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b7cd0b1694422caf04285206f0bd7411ff5de20
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-web-services"></a>Activation des services web
Pour publier des services Web, vous devez configurer les services Internet (IIS), les hôtes BizTalk isolés et les comptes d'utilisateur et de groupe Windows. Cette section explique comment activer les services Web dans IIS. Pour plus d'informations sur l'activation des services Web, consultez la documentation IIS.  
  
 **Services Internet (IIS)**  
  
 Vous pouvez publier des services Web pour les systèmes Windows IIS est configuré avec ASP.NET. Pour chaque serveur, tous les services Web s'exécutent dans le processus de travail ASP.NET.  
  
 Le processus de travail ASP.NET utilise le compte ASPNET local par défaut. IIS utilise des pools d’applications pour le traitement des demandes de service Web.  
  
 **Hôtes BizTalk isolés**  
  
 Pour activer les services Web, vous devez créer au moins un hôte isolé dans BizTalk Server. Les hôtes isolés représentent des processus externes, tels que des extensions ISAPI et des processus ASP.NET qui ne sont ni créés ni contrôlés par BizTalk Server. Ces types de processus externes doivent héberger certains adaptateurs, tels que HTTP/S et SOAP.  
  
 Le Gestionnaire de configuration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée BizTalkServerIsolatedHost que BizTalk utilise comme hôte isolé par défaut. Le groupe Utilisateurs d'hôtes BizTalk isolés est le nom du groupe Windows associé à cet hôte par défaut. Pour plus d’informations sur les hôtes et les Instances d’hôte, consultez [gestion d’hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md).  
  
 Une instance d'hôte isolé ne peut exécuter qu'un seul adaptateur. Si vous configurez les gestionnaires de réception des adaptateurs HTTP et SOAP, avec le seul hôte isolé, vous devez créer deux pools d'applications, soit un pool d'applications par adaptateur.  
  
 Par exemple, si vous envisagez de configurer deux hôtes isolés comme suit :  
  
|Nom de l'hôte isolé|Emplacements de réception|  
|------------------------|-----------------------|  
|Hôte isolé 1|HTTP_ReceiveLocation1A<br /><br /> HTTP_ReceiveLocation1B<br /><br /> SOAP_ReceiveLocation1 **Remarque :** le **hôte isolé 1** est utilisé pour les gestionnaires de réception des adaptateurs SOAP et HTTP.|  
|Hôte isolé 2|HTTP_ReceiveLocation2|  
  
 Vous pouvez créer quatre répertoires virtuels, un par emplacement de réception, comme suit :  
  
|Emplacement de réception|Répertoire virtuel|  
|----------------------|-----------------------|  
|HTTP_ReceiveLocation1A|IIS_Virtual_Directory1A|  
|HTTP_ReceiveLocation1B|IIS_Virtual_Directory1B|  
|SOAP_ReceiveLocation1|IIS_Virtual_Directory1C|  
|HTTP_ReceiveLocation2|IIS_Virtual_Directory2|  
  
 Ensuite, vous devez créer au moins trois pools d'applications pour les répertoires virtuels, comme suit :  
  
> [!NOTE]
>  Vous devez créer au moins un pool d'applications par hôte isolé.  
  
|Répertoires virtuels|Pool d'applications| Description|  
|-------------------------|----------------------|-----------------|  
|IIS_Virtual_Directory1A<br /><br /> IIS_Virtual_Directory1B|AppPool_Host1_HTTP|Un pool d'applications distinct n'est pas requis car tous les emplacements de réception ont le même hôte isolé (Hôte isolé 1) et le même protocole.|  
|IIS_Virtual_Directory1C|AppPool_Host1_SOAP|Un pool d'applications distinct est requis car l'emplacement de réception utilise un protocole différent (SOAP) des autres emplacements de réception dans le même hôte (Hôte isolé 1).|  
|IIS_Virtual_Directory2|AppPool_Host2_HTTP|Un pool d'applications distinct est requis car l'emplacement de réception s'exécute sous un hôte différent de Hôte isolé 1.|  
  
> [!NOTE]
>  Vous devez ajouter le compte d'utilisateur pour les pools d'applications aux groupes locaux ou de domaine appropriés des hôtes isolés. Pour plus d’informations, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
> [!NOTE]
>  Vous devez faire correspondre le compte d’utilisateur entre une instance d’hôte isolé et le pool d’applications correspondant selon les tableaux précédents. Pour plus d’informations sur la relation entre les comptes d’utilisateur des pools d’instance et d’application hôte isolé, consultez [comment modifier les comptes de Service et les mots de passe](../core/how-to-change-service-accounts-and-passwords.md).  
  
 **Accès de base de données pour les installations de serveur unique**  
  
 Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et la base de données de gestion BizTalk résident sur le même serveur, vous devez définir le contexte de l'utilisateur du processus de travail ASP.NET ou du pool d'applications IIS sur le compte d'utilisateur ASPNET local ou un compte d'utilisateur local ou de domaine qui dispose des privilèges minimaux.  
  
 **Accès aux données de plusieurs installations de serveur**  
  
 Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et la base de données de gestion BizTalk résident sur des serveurs différents, vous devez modifier le contexte de l'utilisateur du processus de travail ASP.NET ou du pool d'applications IIS en un compte d'utilisateur de domaine.  
  
 Lors de l'implémentation d'un déploiement de serveur multiples, les groupes Windows Hôte isolé doivent exister sur le domaine auquel appartiennent les serveurs de bases de données BizTalk.  
  
 **Réduction des droits d’utilisateur et des privilèges de compte**  
  
 Vous utilisez des hôtes isolés pour donner aux adaptateurs qui s’exécutent dans l’accès des processus externes au nombre minimal de ressources requises pour interagir avec BizTalk Server. Pour un déploiement sécurisé, vous devez donner les privilèges minimaux au contexte de l'utilisateur pour les processus externes.  
  
 **Recommandations de sécurité de l’Assistant Publication des Services Web BizTalk**  
  
 Le répertoire virtuel créé par l'Assistant Publication de services Web BizTalk hérite des listes de contrôle d'accès (ACL) et des exigences d'authentification du répertoire virtuel parent ou du site Web. Si le répertoire virtuel parent ou le site Web autorise l'accès anonyme, l'Assistant Publication de services Web BizTalk supprime cette fonction lors de la création du répertoire virtuel.  
  
 Le texte suivant contient des notes et des recommandations de sécurité pour [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)].  
  
## <a name="next"></a>Suivant
  
[Comment activer ASP.NET pour les Services Web publiés](../core/how-to-enable-asp-net-4-0-for-published-web-services.md)
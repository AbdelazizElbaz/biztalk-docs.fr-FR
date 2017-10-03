---
title: "Recommandations de sécurité de déploiement application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, applications
- best practices, applications
- best practices, security
- security, best practices
- applications, best practices
- applications, security
ms.assetid: 77902140-8b4c-437c-af4c-10a12b3bc950
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a0402ef23de70150d541dfd672d2af7efe3a924
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="application-deployment-security-recommendations"></a>Recommandations de sécurité liées au déploiement des applications
Cette rubrique présente des directives pour le déploiement d'une application BizTalk dans votre environnement.  
  
-   Toutes les listes de contrôle d'accès discrétionnaires (DACL) sont supprimées des fichiers et dossiers lors de l'exportation d'une application dans un fichier .msi. Une fois l'application installée à partir du fichier .msi, vous devez reconfigurer tous les paramètres de sécurité dans les fichiers et les dossiers.  
  
-   Pour des raisons de sécurité, lorsque vous exportez un fichier de liaison, BizTalk Server ne conserve pas les mots de passe des liaisons du fichier. Une fois les liaisons importées, vous devez reconfigurer les mots de passe des ports d'envoi et des emplacements de réception pour qu'ils fonctionnent. Vous configurez ces mots de passe dans la boîte de dialogue Propriétés du transport de la console Administration de BizTalk Server pour le port d'envoi ou l'emplacement de réception. Pour obtenir des instructions, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Voir aussi [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md). Pour plus d’informations sur les fichiers de liaison, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).  
  
-   Le déploiement ou l'annulation du déploiement d'un schéma de propriété peut exposer des données sensibles, et par la suite les exposer lors du suivi. Chaque fois qu'un assembly contenant un schéma de propriété est déployé ou que son déploiement est annulé, l'observateur d'événements consigne un événement dans le journal des événements des applications Windows. Vous devez rechercher ces messages dans le journal des événements afin de vous assurer que l'ensemble des activités de déploiement d'assembly sont conformes à vos stratégies en matière de traitement des données sensibles.  
  
     Le message généré dans le journal des événements pour le déploiement est :  
  
     **L’utilisateur « {{1} » déployé l’assembly « {0} » qui contient les schémas de propriété.**  
  
     Le message généré dans le journal des événements pour l'annulation du déploiement est :  
  
     **L’utilisateur « {{1} » a annulé déploiement de l’assembly qui contient les schémas de propriété « {0} ».**  
  
-   Si l'application contient un répertoire virtuel, soyez conscient que les paramètres de sécurité du répertoire virtuel utilisés sont ceux qui sont activés lorsque le fichier .msi est généré au cours de l'exportation de l'application. Si vous déployez une application dans un environnement de production, vérifiez que les paramètres répondent à vos exigences en matière de sécurité avant de l'exporter.  
  
     Toutefois, si vous déployez une application comprenant un répertoire virtuel et que le répertoire virtuel existe déjà dans l'environnement de destination, les paramètres de sécurité du répertoire virtuel existant seront utilisés. Ils ne sont pas modifiés afin de correspondre à ceux du répertoire virtuel que vous déployez. Vous devez vérifier qu'ils répondent à vos exigences.  
  
    > [!CAUTION]
    >  Si le répertoire virtuel utilise le protocole HTTPS (Hypertext Transfer Protocol over Secure Socket Layer), ses paramètres de sécurité ne sont pas conservés lors de l'exportation, et lorsqu'il est importé, il hérite de ceux du répertoire racine. Vous devez vérifier que ces paramètres de sécurité répondent à vos exigences.  
  
-   Si le pool d'applications spécifié pour un service Web n'existe pas lorsque vous importez une application, le pool d'applications par défaut est utilisé. Les paramètres de sécurité de ce pool d'applications par défaut peuvent ne pas répondre à vos besoins. Nous vous conseillons donc de créer le pool d'applications et de configurer les paramètres de sécurité appropriés avant l'importation de l'application, ou de vérifier que les paramètres du pool d'applications par défaut vous conviennent.  
  
-   Assurez-vous que vous faites confiance à la source des fichiers du programme d'installation de Windows Installer (.msi) que vous déployez afin d'éviter tous les problèmes de sécurité qui pourraient être générés par des créateurs de fichiers .msi malveillants. Pour plus d’informations, consultez [sécurité et Windows Installer](../core/security-and-windows-installer.md).  
  
-   Vérifiez que vous disposez des autorisations adéquates pour déployer les applications. Pour plus d’informations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
-   Assurez-vous que seuls les administrateurs BizTalk ont accès aux assemblys, fichiers de liaison et fichiers de stratégie, car ils peuvent contenir des données vitales pour l'entreprise, comme les informations sur la connectivité et la configuration. Si vous déployez des applications par le biais d'un partage réseau, configurez la liste de contrôle d'accès discrétionnaire sur le partage réseau de telle sorte que seuls les administrateurs BizTalk puissent voir son contenu. Pour plus d’informations sur les comptes d’utilisateur et de groupe, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
-   Lorsque vous exécutez les tâches de déploiement, BizTalk Server communique avec la base de données de gestion BizTalk. Si ces éléments sont séparés par un pare-feu, vous devez ouvrir les ports appropriés sur le pare-feu entre les domaines de traitement, de services et de données. Pour plus d’informations, consultez [les Ports requis pour BizTalk Server](../core/required-ports-for-biztalk-server.md).  
  
-   Si vous pointez vers un emplacement distant pour un assembly, un fichier de liaison ou un autre fichier de ressources pouvant contenir des données sensibles, assurez-vous de la sécurité du réseau entre l'ordinateur source et l'ordinateur sur lequel vous exécutez le déploiement. Si le réseau entre ces deux ordinateurs n'est pas totalement protégé contre les agresseurs potentiels, copiez le fichier cible sur un support amovible et transportez-le physiquement sur l'ordinateur à partir duquel vous exécutez le déploiement.  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations de sécurité pour le déploiement d’Application](../core/security-considerations-for-application-deployment.md)
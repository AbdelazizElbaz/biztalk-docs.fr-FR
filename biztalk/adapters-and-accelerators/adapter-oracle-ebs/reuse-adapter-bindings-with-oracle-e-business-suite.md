---
title: "Réutiliser les liaisons de l’adaptateur avec Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb4dd90d-7958-4d62-bc7b-d6be16288dbc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25aec8346a4252902e37a778384ae603852a11be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="reuse-adapter-bindings-with-oracle-e-business-suite"></a>Réutiliser les liaisons de l’adaptateur avec Oracle E-Business Suite
Une liaison crée un mappage entre un point de terminaison logique (par exemple, un port d’orchestration ou un lien de rôle) et un point de terminaison physique (par exemple un envoi et le port de réception). Cela permet la communication entre les différents composants d’un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution d’entreprise. Vous pouvez créer des liaisons à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
## <a name="what-is-a-binding-file"></a>Qu’est un fichier de liaison ?  
 Un fichier de liaison est un fichier XML qui contient des informations de liaison pour chaque orchestration BizTalk dans l’étendue d’un assembly BizTalk, une application ou un groupe. Le fichier de liaison décrit :  
  
-   L’hôte auquel est liée chaque orchestration.  
  
-   Le niveau de confiance de l’hôte.  
  
-   Les paramètres pour chaque port d’envoi, port de réception, l’emplacement de réception et tiers qui a été configuré.  
  
 Vous pouvez générer des fichiers de liaison, puis appliquez les liaisons qu’ils contiennent à un assembly, une application ou un groupe. Cela évite d’avoir à configurer manuellement les liaisons dans différents environnements de déploiement et accélère le déploiement de l’application.  
  
 Un fichier de liaison n’est pas généré automatiquement pour un assembly, une application ou un groupe BizTalk. Toutefois, vous pouvez générer un fichier de liaison en exportant des liaisons. De même, vous pouvez ensuite importer le fichier de liaison dans une application ou un groupe. Cette section fournit des instructions sur la façon d’importer et exporter des liaisons.  
  
 Pour plus d’informations sur les liaisons et les fichiers de liaison, consultez [déploiement d’applications et des fichiers de liaison](../../core/binding-files-and-application-deployment.md).

 > [!NOTE]
 >  Un fichier de liaison n’est pas généré automatiquement pour un assembly, une application ou un groupe BizTalk. Mais vous pouvez générer un fichier de liaison en exportant des liaisons. Vous pouvez ensuite importer le fichier de liaison dans une application ou un groupe.  
 
## <a name="prerequisites"></a>Conditions préalables    
Connectez-vous vec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs ou opérateurs BizTalk. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).

## <a name="export-bindings"></a>Exporter les liaisons

Cette section décrit comment exporter des liaisons pour une application BizTalk dans un fichier XML. Vous pouvez ensuite importer les liaisons à partir du fichier XML dans une autre application BizTalk. Importation des liaisons remplace les liaisons existantes portant le même nom dans l’application. Vous pouvez aussi ajouter des liaisons à une application, ce qui n'écrase pas les liaisons existantes. Les liaisons ajoutées ne prennent effet qu'une fois l'application importée.  

1.  Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Développez **groupe BizTalk**, puis développez **Applications**.  
  
3.  Cliquez sur l’application dont les liaisons à exporter, sélectionnez **exporter**, puis sélectionnez **liaisons**.  
  
4.  Sur le **exporter les liaisons** page **exportation vers le fichier**, tapez le chemin d’accès absolu du fichier XML vers lequel exporter les liaisons.  
  
     Par exemple, entrez`C:\Bindings\Application1Bindings.Binding1.xml`  
  
5.  Vérifiez que **exporter toutes les liaisons à partir de l’application actuelle** est sélectionnée.  
  
6.  Pour exporter toutes les informations de tiers pour le groupe, sélectionnez le **informations d’exportation de tiers Global** case à cocher.  
  
7.  Sélectionnez **OK**. Les liaisons sont exportées dans un fichier XML à l’emplacement que vous avez spécifié.  

## <a name="import-bindings"></a>Importer les liaisons

Importer des liaisons à l’aide de la console Administration de BizTalk Server.
  
1.  Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Développez **groupe BizTalk**, puis développez **Applications**.  
  
3.  Cliquez sur l’application dans laquelle vous souhaitez importer des liaisons, sélectionnez **importer**, puis sélectionnez **liaisons**.  
  
4.  Sélectionnez le fichier de liaison, puis **ouvrir**.  
  
Les artefacts du fichier de liaison sont écrits dans l'application. Ils s'affichent dans les dossiers appropriés de l'application. Par exemple, les ports d’envoi importés dans le cadre de l’affichage de liaisons sous le **Ports d’envoi** dossier.  
  
## <a name="passwords-are-removed"></a>Les mots de passe sont supprimés.  
Pour des raisons de sécurité, lorsque vous exportez un fichier de liaison, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] supprime les mots de passe pour les liaisons du fichier. Une fois les liaisons importées, vous devez reconfigurer les mots de passe des ports d'envoi et des emplacements de réception pour qu'ils fonctionnent. Vous configurez les mots de passe dans la boîte de dialogue Propriétés du Transport de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] l’Administration de la console pour le port d’envoi ou emplacement de réception. 

Pour plus d’informations sur la spécification du nom d’utilisateur et mots de passe, consultez [configurer les informations d’identification de connexion d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-sign-in-credentials-for-the-oracle-e-business-suite.md).
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)
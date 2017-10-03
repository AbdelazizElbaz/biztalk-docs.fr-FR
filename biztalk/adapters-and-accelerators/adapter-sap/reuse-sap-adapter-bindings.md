---
title: "Réutiliser les liaisons de l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding file, definition
- adapter bindings, reusing
ms.assetid: 5748c22f-20a2-4eb9-ad45-a1bef7290802
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df4c878f8eb6a5e1fd52dfe749b10d1d89716679
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="reuse-sap-adapter-bindings"></a>Réutiliser les liaisons de l’adaptateur SAP
Une liaison crée un mappage entre un point de terminaison logique (par exemple, un port d’orchestration ou un lien de rôle) et un point de terminaison physique (par exemple un envoi et le port de réception). Elle permet aux différents composants d'une solution d'entreprise BizTalk de communiquer. Vous pouvez créer des liaisons dans la console Administration de BizTalk Server.  
  
## <a name="what-is-a-binding-file"></a>Qu’est un fichier de liaison ?  
 Un fichier de liaison est un fichier XML qui contient des informations de liaison pour chaque orchestration BizTalk dans l’étendue d’un assembly BizTalk, une application ou un groupe. Le fichier de liaison décrit :  
  
-   L’hôte auquel est liée chaque orchestration
  
-   Le niveau de confiance de l’hôte
  
-   Les paramètres pour chaque port d’envoi, port de réception, emplacement de réception et tiers qui a été configuré
  
 Vous pouvez générer des fichiers de liaison, puis appliquez les liaisons qu’ils contiennent à un assembly, une application ou un groupe. Cela évite d’avoir à configurer manuellement les liaisons dans différents environnements de déploiement et accélère le déploiement de l’application.  
  
Un fichier de liaison n’est pas généré automatiquement pour un assembly, une application ou un groupe BizTalk. Toutefois, vous pouvez générer un fichier de liaison en exportant des liaisons. Vous pouvez ensuite importer le fichier de liaison dans une application ou un groupe.  
  
Pour plus d’informations sur les liaisons et les fichiers de liaison, consultez [déploiement d’applications et des fichiers de liaison](../../core/binding-files-and-application-deployment.md).
  
## <a name="prerequisites"></a>Conditions préalables  
Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs ou opérateurs BizTalk. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).
 
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

Pour plus d’informations sur la spécification du nom d’utilisateur et mots de passe, consultez [configurer l’authentification dans les informations d’identification pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-the-sign-in-credentials-for-the-sap-system.md).

## <a name="see-also"></a>Voir aussi
[Blocs de construction pour créer des applications SAP](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)
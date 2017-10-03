---
title: Importation de liaison DAT3 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, importing
- target computer, cleaning
- importing binding files
- cleaning target computer
ms.assetid: 955bb3e1-3dbc-43ce-9126-205d838ae662
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa1d95c40e3e556068e15a269ee4cbb7e995429a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-binding-files"></a>importation des fichiers de liaison
Avant d’utiliser le serveur BizTalk pour importer un fichier de liaison, vérifiez les éléments suivants :  
  
-   CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à JD Edwards. Vérifiez que l'emplacement de ces fichiers est identique sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.  
  
-   Les dossiers pour les réponses existent et sont identiques sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.  
  
-   S'ils sont présents dans la configuration, les mots de passe du système JD Edwards sont enregistrés dans le fichier de liaison sous la forme *****. Pour plus d’informations, consultez [limitations concernant le déploiement](../core/deployment-limitations2.md).  
  
> [!NOTE]
>  Déploiement remplace la configuration de l’emplacement de réception. Lors du déploiement d'un fichier de liaison (et de l'assembly) sur un ordinateur cible, les ports d'envoi et les emplacements de réception sont remplacés par ceux qui se trouvent dans le fichier de liaison XML lors de leur importation.  
  
## <a name="importing-the-binding-files"></a>Importation des fichiers de liaison  
 La procédure suivante permet d'importer les fichiers de liaison.  
  
#### <a name="to-import-the-binding-files"></a>Pour importer les fichiers de liaison  
  
1.  Sur le **Démarrer** menu, pointez sur **Program Files**, pointez sur **Microsoft BizTalk Server**, puis cliquez sur **Administration de BizTalk Server** Pour démarrer la Console Administration de BizTalk Server.  
  
2.  Développez successivement Administration de BizTalk Server, **groupe BizTalk**, puis développez **Applications**.  
  
3.  Cliquez sur l’application souhaitée, pointez sur **importation**, puis cliquez sur **liaisons**.  
  
4.  Dans le **importer les liaisons** boîte de dialogue Parcourir et sélectionner les fichiers de liaison, puis cliquez sur **ouvrir**.  
  
## <a name="cleaning-the-target-computer"></a>Nettoyage de l'ordinateur cible  
 La procédure suivante permet de nettoyer l'ordinateur cible.  
  
#### <a name="to-clean-the-target-computer"></a>Pour nettoyer l'ordinateur cible  
  
-   Supprimez les ports d’envoi et les emplacements de réception qui sont liés à l’orchestration.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires de JD Edwards OneWorld envoi](../core/creating-jd-edwards-oneworld-send-handlers.md)   
 [Déploiement de Ports et assemblys](../core/deploying-ports-and-assemblies4.md)
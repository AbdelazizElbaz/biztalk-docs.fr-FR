---
title: "Importer des schémas de JD Edwards EnterpriseOne dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 640d5884-953a-46b6-b9dc-b931392a3059
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acd61cc8ab63d6859a8e10afb76f93c2f8cb2150
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="importing-schemas-into-biztalk-server-projects"></a>Importation de schémas dans des projets BizTalk Server
Cette section décrit la navigation sur un serveur JD Edwards EnterpriseOne et l'importation des schémas dans un projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  Vous devez vérifier que vous avez défini le fichier arglist. Vous devez mettre à jour le fichier jdearglist.txt avant de générer les schémas dans l'orchestration. Pour plus d’informations, consultez [gestion des valeurs de chaîne](../core/handling-string-values2.md).  
  
> [!NOTE]
>  Chaque fois que vous modifiez le fichier jdearglist, vous devez régénérer les schémas pour cet objet métier.  
  
 Après la création du port JD Edwards EnterpriseOne, vous pouvez explorer JD Edwards EnterpriseOne en lançant l'Assistant Adaptateur Microsoft à partir d'un projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="import-schemas-into-visual-studio"></a>Importer des schémas dans Visual Studio
  
1.  Ouvrez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2.  Cliquez sur le nom de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de projet, pointez sur **ajouter**, puis sélectionnez **ajouter les éléments générés**.  
  
3.  Cliquez sur **ajouter** pour ouvrir le **Assistant Ajout d’adaptateur**.  
  
4.  Sur le **sélectionner un adaptateur** page, sélectionnez le nom de la carte pour laquelle vous souhaitez importer des schémas (par exemple, **JDEEnterpriseOne**).  
  
5.  Dans le **SQL Server** , sélectionnez un serveur SQL server.  
  
6.  Dans le **base de données** , sélectionnez une base de données.  
  
     La base de données par défaut est la même que votre serveur SQL Server.  
  
7.  Dans le **Port** zone, sélectionnez un serveur SQL server, puis cliquez sur **suivant**.  
  
     Le système JD Edwards EnterpriseOne apparaît dans le navigateur.  
  
8.  Continuez avec la procédure suivante ci-dessous.  
  
 L'Assistant Ajout d'adaptateur affiche une arborescence des systèmes définis. JD Edwards EnterpriseOne inclut plusieurs modules. Les modules sont regroupés selon les trois premiers caractères de leur nom.  
  
-   Le premier niveau de la hiérarchie correspond à la liste des préfixes à trois caractères des noms de module.  
  
-   Le second niveau inclut les modules qui partagent le même préfixe à trois caractères.  
  
-   Le dernier niveau répertorie les fonctions commerciales appartenant à un module. Lorsque vous développez l'icône des services, vous pouvez afficher ses opérations.  
  
 Le développement d'une opération affiche les arguments d'entrée/de sortie. Vous pouvez développer les arguments d'entrée/de sortie pour afficher les types de données des arguments.  
  
> [!NOTE]
>  Si les définitions d'objet serveur sont modifiées, vous devez régénérer le schéma afin d'actualiser les données qu'il contient.  
  
> [!NOTE]
>  Si vous modifiez le fichier jdearglist.txt après avoir généré votre schéma, vous devez régénérer le schéma pour actualiser les données qu'il contient. Pour plus d’informations sur le fichier jdearglist.txt, consultez [gestion des valeurs de chaîne](../core/handling-string-values2.md).  
  
## <a name="select-the-schemas"></a>Sélectionner les schémas  
  
1.  Dans le **sélectionner les Services à importer** page, développez le nœud de niveau supérieur de la **des objets métier** nœud ou la **Services professionnels** nœud.  
  
2.  Activez la case à cocher en regard des éléments que vous souhaitez importer, puis cliquez sur **OK**.  
  
3.  Les schémas générés pour les éléments JD Edwards EnterpriseOne sélectionnés sont importés dans votre projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  Lors de l’utilisation de carnet d’adresses (N0100041) le nom du champ est **cActionCode**. L'action fait partie du fichier XML lui-même. Les codes suivants sont utilisés :  
  
-   A pour ajouter ;  
  
-   C pour modifier ;  
  
-   D pour supprimer ;  
  
-   I pour demande.  
  
## <a name="next-step"></a>Étape suivante
[Utiliser des propriétés de contexte de message](../core/using-message-context-properties1.md)
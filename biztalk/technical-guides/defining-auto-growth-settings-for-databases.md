---
title: "Définition des paramètres de croissance automatique pour les bases de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd86dd49-6505-4673-b413-d3af729dfca9
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d702898cdaab8f9993fdc9b901e34f51ba6941c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-auto-growth-settings-for-databases"></a>Définition des paramètres de croissance automatique pour les bases de données
Vous devez définir la croissance automatique de la base de données sur un nombre fixe de mégaoctets au lieu d’un pourcentage, en particulier pour les bases de données MessageBox et des suivis BizTalk. Selon votre application BizTalk et le débit, la MessageBox et le suivi des bases de données peuvent devenir très volumineux. Si vous définissez la croissance automatique sur un pourcentage, puis la croissance automatique peut être substantielle.  
  
## <a name="how-instant-file-initialization-works"></a>Instantanés comment fonctionne l’initialisation de fichier  
 Lorsque SQL Server augmente la taille d’un fichier, il doit d’abord initialiser le nouvel espace avant de pouvoir être utilisé. Il s’agit d’une opération de blocage qui implique le remplissage du nouvel espace de pages vides. [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)]ou version ultérieure en cours d’exécution sur Windows Server 2003 ou version ultérieure prend en charge les « initialisation instantanée des fichiers. » Cela peut considérablement réduire l’impact sur les performances d’une opération de croissance de fichier. Pour plus d’informations, consultez [« Initialisation du fichier de base de données »](http://go.microsoft.com/fwlink/?LinkId=101579) (http://go.microsoft.com/fwlink/?LinkId=101579) dans la documentation de SQL Server. Cette rubrique décrit les étapes qui doivent être prises pour activer l’initialisation instantanée des fichiers.  
  
## <a name="enabling-instant-file-initialization"></a>Activer l’initialisation instantanée des fichiers  
 Pour les étapes de l’activation instantanée de fichiers d’initialisation, consultez [« Initialisation du fichier de base de données »](http://go.microsoft.com/fwlink/?LinkId=101579) (http://go.microsoft.com/fwlink/?LinkId=101579) dans la documentation de SQL Server. Pour créer des groupes de fichiers et le déplacement de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des tables de base de données, les index et les fichiers journaux dans les groupes de fichiers approprié, suivent les recommandations de « Annexe B – recommandé de base de données de Configuration de BizTalk Server » dans le [« BizTalk Livre blanc de l’optimisation du serveur de base de données »](http://go.microsoft.com/fwlink/?LinkID=101578) (http://go.microsoft.com/fwlink/?LinkID=101578). Dans l’idéal, la taille des fichiers de prise en charge les groupes de fichiers doit être pré-allouée et si possible, affectez à une taille fixe.  
  
 Si le système est nouveau et les tailles statiques n’ont pas été établies définitivement, puis configurez des fichiers avec la **activer la croissance automatique** option et spécifiez la croissance des fichiers **en mégaoctets**. L’incrément de croissance doit généralement pas être supérieur à 100 Mo (pour les fichiers volumineux), 10 Mo (pour les fichiers de taille moyenne) ou 1 Mo (pour les petits fichiers).
---
title: "Définir les paramètres de croissance automatique de bases de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd86dd49-6505-4673-b413-d3af729dfca9
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d37bcce2d60167496bc55a12c65a488db17fceb
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="define-auto-growth-settings-for-databases"></a>Définir les paramètres de croissance automatique de bases de données
Vous devez définir la croissance automatique de la base de données sur un nombre fixe de mégaoctets au lieu d’un pourcentage, en particulier pour les bases de données MessageBox et des suivis BizTalk. Selon votre application BizTalk et le débit, la MessageBox et le suivi des bases de données peuvent devenir très volumineux. Si vous définissez la croissance automatique sur un pourcentage, puis la croissance automatique peut être substantielle.  
  
## <a name="how-instant-file-initialization-works"></a>Instantanés comment fonctionne l’initialisation de fichier  
 Lorsque SQL Server augmente la taille d’un fichier, il doit d’abord initialiser le nouvel espace avant de pouvoir être utilisé. Il s’agit d’une opération de blocage qui implique le remplissage du nouvel espace de pages vides. SQL Server sur Windows prend en charge le « initialisation instantanée des fichiers. » Cela peut considérablement réduire l’impact sur les performances d’une opération de croissance de fichier. Pour plus d’informations, consultez [Initialisation des fichiers de base de données](https://docs.microsoft.com/sql/relational-databases/databases/database-instant-file-initialization). Cette rubrique décrit les étapes qui doivent être prises pour activer l’initialisation instantanée des fichiers.  
  
## <a name="enable-instant-file-initialization"></a>Activer l’initialisation instantanée des fichiers  
 Pour les étapes de l’activation instantanée de fichiers d’initialisation, consultez [l’initialisation des fichiers de base de données](https://docs.microsoft.com/sql/relational-databases/databases/database-instant-file-initialization). Pour créer des groupes de fichiers et déplacement de tables de base de données BizTalk Server, les index et les fichiers journaux dans les groupes de fichiers approprié, suivez les recommandations de la [guide d’optimisation des performances BizTalk](../technical-guides/biztalk-server-2013-performance-optimization-guide.md). Dans l’idéal, la taille des fichiers de prise en charge les groupes de fichiers doit être pré-allouée et si possible, affectez à une taille fixe.  
  
 Si le système est nouveau et les tailles statiques n’ont pas été établies définitivement, puis configurez des fichiers avec la **activer la croissance automatique** option et spécifiez la croissance des fichiers **en mégaoctets**. L’incrément de croissance doit généralement pas être supérieur à 100 Mo (pour les fichiers volumineux), 10 Mo (pour les fichiers de taille moyenne) ou 1 Mo (pour les petits fichiers).

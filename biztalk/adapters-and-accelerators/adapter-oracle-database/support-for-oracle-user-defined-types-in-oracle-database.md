---
title: "Prise en charge pour les Types définis par l’utilisateur Oracle dans la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68edf0f2-a798-4096-86ca-85d2cfa9088a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8c4f29ce8b11f74db5ff7a145449f7f212f6f6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="support-for-oracle-user-defined-types-in-oracle-database"></a>Prise en charge pour les Types définis par l’utilisateur Oracle dans la base de données Oracle
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] prend en charge l’exécution d’opérations sur les artefacts dans la base de données Oracle qui contiennent des Types de Oracle User-Defined (UDT). Les UDT peuvent être présents dans les artefacts suivants :  
  
-   Tables et des vues contenant les colonnes UDT.  
  
-   Les packages, les procédures stockées et les fonctions contenant les paramètres UDT.  
  
## <a name="what-is-an-oracle-udt"></a>Qu’est un UDT Oracle ?  
 Les UDT Oracle aident dans la représentation des entités complexes qu’un objet « unique » qui peut être partagé entre les applications. Par exemple, il est possible d’entités réel du modèle telles que « Customers » ou « Sales Orders » en tant qu’objets dans la base de données Oracle. Oracle UDT sont définis dans la base de données Oracle, et ils sont de deux types suivants :  
  
-   Types d’objets. Par exemple, objet Oracle.  
  
-   Types de collection. Par exemple, les types de table imbriquée ou VARRAY.  
  
 Le nom de l’UDT Oracle respecte la casse et doit être spécifié de la façon suivante : [nom_schéma]. [UDT_NAME].  
  
## <a name="how-does-the-adapter-support-oracle-udt"></a>Comment l’adaptateur prend en charge Oracle UDT ?  
 ODP.NET prend en charge les UDT en représentant les types UDT Oracle défini dans la base de données Oracle en tant que types de .NET (types personnalisés). Types personnalisés définissant le mappage entre les attributs de l’UDT d’Oracle ou les éléments pour les membres de .NET. Types personnalisés peuvent être des classes .NET ou les structures et peuvent représenter des objets Oracle ou Collections d’Oracle.  Du fait que le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ODP.NET pour se connecter à la base de données Oracle, il hérite de la prise en charge pour les UDT d’Oracle.  
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise le ODP.NET pour spécifier un mappage de type personnalisé pour mapper un type personnalisé .NET à un UDT Oracle dans la base de données. Pour spécifier un mappage de type personnalisé, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise une fabrique de type personnalisé. Par conséquent, un assembly (fichier .dll) est requis pour pouvoir utiliser un UDT Oracle, qui définit la fabrique de type personnalisé. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] vous permet de générer un assembly de la fabrique de type personnalisé lors de la génération de métadonnées pour une artefact/opération qui contient un UDT Oracle.  
  
> [!NOTE]
>  L’adaptateur génère l’assembly pour les UDT Oracle basé sur les classes utilisées par la ODP.NET pour prendre en charge Oracle UDT. Pour obtenir des informations détaillées sur la façon dont les types UDT Oracle sont prises en charge ODP.NET, consultez [http://go.microsoft.com/fwlink/?LinkId=140697](http://go.microsoft.com/fwlink/?LinkId=140697).  
  
 Pour générer le fichier d’assembly pour l’utilisation de l’UDT Oracle au moment du design et l’utiliser ultérieurement au niveau de l’exécution, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose les propriétés de liaison suivantes :  
  
-   **GeneratedUserTypesAssemblyFilePath** (au moment du design)  
  
-   **GeneratedUserTypesAssemblyKeyFilePath** (au moment du design)  
  
-   **UserAssembliesLoadPath** (temps d’exécution)  
  
 Pour plus d’informations sur ces propriétés de liaison, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
## <a name="performing-operations-on-artifacts-containing-oracle-udts"></a>Opérations sur les artefacts qui contient les types UDT Oracle  
 Pour effectuer des opérations sur les artefacts contenant des UDT à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], vous devez effectuer les opérations suivantes au moment du design et le moment de l’exécution.  
  
### <a name="design-time"></a>Moment de la conception  
 Vous devez effectuer ces étapes lors de schéma de génération pour l’opération dans Visual Studio.  
  
1.  Se connecter à la base de données Oracle à l’aide du [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Pour plus d’informations, consultez [se connecter à la base de données Oracle dans Visual Studio à l’aide de Consume Adapter Service](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-in-visual-studio-using-the-consume-adapter-service.md).  
  
2.  Lors de la connexion, dans le **propriétés de liaison** onglet de la **configurer l’adaptateur** boîte de dialogue, spécifiez les valeurs appropriées pour le **GeneratedUserTypesAssemblyFilePath** et **GeneratedUserTypesAssemblyKeyFilePath** propriétés de liaison. Pour plus d’informations sur ces propriétés de liaison, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
3.  Lorsque vous êtes connecté à la base de données Oracle dans Visual Studio, accédez à l’artefact requis qui contient un UDT Oracle. Pour plus d’informations sur la consultation des artefacts, consultez [Parcourir, rechercher et d’obtenir les métadonnées pour les opérations de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/browse-search-and-get-metadata-for-oracle-database-operations.md).  
  
4.  Sélectionnez l’artefact requis, puis cliquez sur **OK**. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] génère les métadonnées pour l’opération sélectionnée, ainsi que l’assembly (fichier .dll) pour l’UDT Oracle dans l’objet sélectionné. L’assembly est créé à l’emplacement que vous avez spécifié dans le **GeneratedUserTypesAssemblyFilePath** propriété de liaison.  
  
5.  Continuer avec le reste des étapes de génération et le déploiement de votre projet.  
  
### <a name="run-time"></a>Moment de l'exécution  
 Vous devez effectuer ces étapes dans les clients de la carte pour effectuer des opérations sur les UDT Oracle.  
  
 **Dans BizTalk Server**  
  
-   Ajouter manuellement l’assembly UDT d’Oracle créé à l’étape 4 dans le « Temps de conception » pour le Global Assembly Cache (GAC) sur votre ordinateur. Ou bien, vous pouvez copier manuellement l’assembly UDT d’Oracle sous l’emplacement d’installation de BizTalk Server. Pour [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], il s’agit généralement \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].  
  
-   Lors de la configuration du [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] WCF-Custom ou WCF-OracleDB de port, dans le **liaison** onglet, spécifiez l’emplacement de l’assembly UDT d’Oracle pour le **UserAssembliesLoadPath** propriété de liaison. Pour plus d’informations sur cette propriété de liaison, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
 **Dans Visual Studio**  
  
-   Ajouter manuellement l’assembly UDT d’Oracle créé à l’étape 4 dans le « Temps de conception » pour le Global Assembly Cache (GAC) sur votre ordinateur. Ou bien, vous pouvez copier manuellement l’assembly UDT d’Oracle vers le même emplacement que le fichier exécutable projet, qui est généralement dans le dossier \bin\Debug du projet.  
  
-   Spécifiez l’emplacement de l’assembly UDT d’Oracle pour le **UserAssembliesLoadPath** propriété de liaison. Pour plus d’informations sur cette propriété de liaison, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)
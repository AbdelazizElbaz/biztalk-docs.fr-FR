---
title: Limitations de l’adaptateur BizTalk pour base de données Oracle | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapter, limitations of
ms.assetid: eab4ddea-f986-43c2-82bb-b9fe37961a5b
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd6cfea523333752c0ee18fefbc6a1848057fe36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-of-biztalk-adapter-for-oracle-database"></a>Limitations de l’adaptateur BizTalk pour base de données Oracle
## <a name="general"></a>Général  
 Les éléments suivants sont connus limitations pour les [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]:  
  
-   Interdiction de quelques exceptions près, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est compatible avec la version précédente des adaptateurs. Pour obtenir la liste des modifications qui s’est produit depuis la dernière version, consultez [principales fonctionnalités de l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/key-features-in-biztalk-adapter-for-oracle-database.md).  
  
-   Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge les Types XML.  
  
-   L’opération SQLEXECUTE ne retourne pas de valeurs pour l’ou les paramètres dans les procédures, les fonctions ou les packages. Pour cette raison, vous devez appeler des procédures, fonctions et des packages en utilisant les opérations dédiées qui le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose pour que ces artefacts Oracle.  
  
-   Lors de la récupération des données à partir de la base de données Oracle à l’aide du proxy de programmation, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne désérialise pas les messages XML qui ont plus de 65 536 nœuds. Vérifiez que le message de réponse a des nœuds est inférieur ou égal à 65 536. Vous pouvez contourner cette limitation en modifiant le fichier app.config de votre application. Pour obtenir des instructions, consultez [résoudre les problèmes opérationnels avec l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-operational-issues-with-the-oracle-database-adapter.md).  
  
-   Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend entrée chaînes et construit les commandes SQL qui sont ensuite exécutées par l’adaptateur. Toutefois, la chaîne d’entrée peut contenir des autres commandes SQL qui également exécutées et risque de perturber le contrat d’opération.  
  
     Considérez un scénario dans lequel l’adaptateur fournit une entrée REF CURSOR à une procédure stockée. Dans ce scénario, le client de l’adaptateur doit fournir une commande qui, lors de l’exécution, obtient le REF CURSOR. L’adaptateur transmet ensuite sur le REF CURSOR à la procédure stockée. Toutefois, si la commande permettant d’obtenir le REF CURSOR effectue certaines modifications supplémentaires pour la base de données, le contrat d’opération pour l’exécution de la procédure stockée est rompu.  
  
-   Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge jusqu'à deux niveaux d’imbrication des UDT.  
  
-   Lorsque vous utilisez les adaptateurs avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], si les informations d’identification sur WCF-custom envoie de port sont incorrectes, les messages de demande ne sont pas traités. Après avoir spécifié les informations d’identification correctes, le message est envoyé à la base de données Oracle et une réponse est reçue. Toutefois, le message de réponse n’est pas disponible pour le port de sortie. Dans de tels scénarios, vous devrez peut-être redémarrer l’instance d’hôte.  
  
-   Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge le type de données BFILE à l’intérieur des types complexes (telles que l’enregistrement type, TABLE type, UDT et VARRAY).  
  
-   Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge les Types définis par l’utilisateur (UDT) qui ont des références circulaires.  
  
-   Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne pas les enregistrements de prise en charge qui contiennent des champs de type de tables PL/SQL de type d’enregistrement.  
  
-   Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne pas autoriser les clients à définir la valeur du premier élément dans un VARRAY avec la valeur NULL.  
  
-   À l’exception des tables de PL/SQL, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge les UDT sont définis à l’intérieur d’un package.  
  
## <a name="limitations-due-to-odpnet"></a>Limitations en raison de ODP.NET  
 Les éléments suivants sont connus limitations pour les [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] en raison de la limitation de ODP.NET :  
  
-   Pour les types de données Oracle qui acceptent des valeurs décimales, ODP.NET ne lève pas d’exception si la valeur d’entrée contient des caractères alphabétiques. Étant donné que le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise ODP.NET pour interagir avec la base de données Oracle, l’adaptateur trop ne lève pas d’exception lors du passage des caractères alphabétiques. Exemple :  
  
    -   Passage d’une valeur « 54r » pour une opération d’insertion ne lève pas d’exception ; la valeur « 54 » est insérée à la place.  
  
    -   Passage d’une valeur « r » 54 pour une opération d’insertion ne lève pas d’exception ; la valeur « 0 » est insérée à la place.  
  
-   En raison d’une limitation ODP.NET, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge l’utilisation de procédures surchargées à l’aide de fortement typée et faiblement typée REF CURSOR. En interne, l’adaptateur traite les curseurs REF fortement typée et faiblement typée en tant que simplement REF CURSOR.  
  
-   Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge les tables PL/SQL qui ne sont pas indexés par un champ numérique.  
  
-   Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge les tableaux associatifs qui ne contiennent pas de n’importe quel élément.  
  
-   Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge les UDT qui contiennent le type de données TimeStamp avec les attributs de fuseau horaire local (TimeStampLTZ).  
  
-   Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge les UDT qui contiennent un «. » (point) dans leurs noms.  
  
-   Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge les UDT qui contiennent des types de données objet BLOB, CLOB et NCLOB en tant que paramètre IN OUT.  
  
-   Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge Varray de Varray des types simples suivants : BFILE, IntervalDS, IntervalYM, TimeStampLTZ et TimeStampTZ.  
  
-   En raison de la limitation d’associatifs, les tables de PL/SQL ou PL/SQL d’enregistrements qui contiennent un des types de données suivants ne sont pas gérées dans le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]:  
  
    -   BFILE  
  
    -   BLOB  
  
    -   CLOB  
  
    -   IntervalDS  
  
    -   IntervalYM  
  
    -   Long  
  
    -   NCLOB  
  
    -   ID de ligne  
  
    -   TimeStamp  
  
    -   TimeStampLTZ  
  
    -   TimeStampTZ  
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)
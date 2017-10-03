---
title: "Opérations sur les synonymes dans la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 608e8c36-ac78-4d7d-aca4-be552505fc2b
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 006107f5f21d017a79b7aa11f70fb1728bb5639a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-synonyms-in-oracle-database"></a>Opérations sur les synonymes dans la base de données Oracle
Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] permet d’effectuer des opérations sur les synonymes. Un synonyme est un alias ou un nom convivial pour les objets de base de données (par exemple, les tables, vues, procédures stockées, fonctions et packages). Pour plus d’informations sur les synonymes dans Oracle, consultez [http://go.microsoft.com/fwlink/?LinkId=138058](http://go.microsoft.com/fwlink/?LinkId=138058).  
  
## <a name="advantages-of-using-synonyms"></a>Avantages de l’utilisation de synonymes  
 Les synonymes sont utiles dans les scénarios suivants :  
  
-   **Utilisation des schémas différents**: Si vous travaillez avec des schémas différents et devoir accéder aux objets entre schémas, vous devez utiliser les différentes instructions SQL pour accéder à ces objets. Vous pouvez créer un synonyme pour un objet dans un schéma et utiliser le synonyme dans votre instruction SQL pour accéder à l’objet. Si vous avez besoin pour accéder à l’objet sous-jacent dans un schéma différent, modifiez la définition du synonyme pour pointer vers l’objet dans un schéma différent. Par conséquent, les applications basées sur le synonyme continuent à fonctionner sans modification dans l’instruction SQL.  
  
     Par exemple, supposons que vous avez deux schémas identiques pour vos environnements de test et de production : « Test » et « Production ». Pour accéder à une table appelée « Employee » dans le schéma de « Test », vous devez utiliser `Test.Employee` ou `Employee` (Si « Test » est le schéma par défaut) dans votre instruction SQL. Si vous souhaitez utiliser le tableau « Employee » dans le schéma de production, vous devez maintenant utiliser `Prod.Employee` ou `Employee` (remplacez le schéma par défaut « Production ») dans votre instruction SQL. Pour contourner ce problème, vous pouvez créer un synonyme pour la table « Test.Employee » (par exemple « EMP ») et utiliser ensuite dans vos instructions SQL. Chaque fois que vous avez besoin effectuer l’opération sur la table « Prod.Employee », modifiez la définition du synonyme « EMP » afin qu’il pointe vers la table « Prod.Employee ». Cela garantit que vous n’êtes pas obligé de modifier vos instructions SQL pour effectuer l’opération sur l’objet dans des schémas différents.  
  
-   **Modifications dans les objets sous-jacents**: les synonymes vous protègent pas contre les modifications dans le nom ou l’emplacement des objets sous-jacents sur lequel vous effectuez une opération. Vous pouvez modifier la définition de synonyme pour prendre en compte les modifications dans le nom ou l’emplacement des objets sous-jacents.  
  
     Par exemple, supposons que vous utilisez une table dans un de vos procédures stockées. Maintenant, si les changements de nom de table ou de la table est déplacée vers un autre emplacement puis votre procédure stockée cessera de fonctionner. Pour contourner ce problème, vous pouvez utiliser un synonyme de la table dans la procédure stockée et mettre à jour la définition de synonyme s’il existe une modification dans le nom ou l’emplacement de la table.  
  
-   **Un accès simplifié et sécurisé**: dans un environnement distribué, vous devez utiliser le nom de schéma, ainsi que les noms des objets pour vous assurer que vous accédez à l’objet correct. En outre, vous devez également vous assurer que l’utilisateur a besoin de privilèges sur l’objet cible. Pour simplifier cela, vous pouvez attribuer un nom simple pour un objet en créant un synonyme qui a le chemin d’accès qualifié complet à l’objet et puis accorder des privilèges appropriés sur le synonyme.  
  
## <a name="working-with-synonyms-in-the-adapter"></a>Utilisation des synonymes dans l’adaptateur  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose les synonymes dans Oracle pour :  
  
-   Tables  
  
-   Vues  
  
-   Procédures stockées  
  
-   Fonctions  
  
-   .  
  
 Les synonymes de chacun de ces artefacts sont exposés en même temps que l’objet sous-jacent respectif dans le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], et [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]. Par exemple, le **Table** nœud sous un schéma affiche tous les synonymes pour les tables, ainsi que les tables de base de données dans un schéma, le **vue** affiche tous les synonymes pour les vues le long de nœud sous un schéma avec les vues de la base de données dans un schéma et ainsi de suite.  
  
-   Les synonymes créés sur les tables et les vues, les mêmes opérations sont exposées comme pour les tables sous-jacentes et les vues respectivement. Par exemple, si les tables et les vues sous-jacentes contiennent des colonnes LOB, les synonymes pour les tables et les vues expose également les opérations ReadLOB et UpdateLOB.  
  
-   Les synonymes créés sur les packages, des fonctions et des procédures stockées, les synonymes sont exposés en tant qu’opérations en même temps que les procédures stockées sous-jacentes, les fonctions et les packages dans un schéma.  
  
> [!NOTE]
>  Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge uniquement les synonymes locales. Cela implique que seuls les synonymes sont pris en charge par l’adaptateur qui ciblent les artefacts sur le serveur local.  
  
 En outre, les actions de message pour les synonymes sont les mêmes que l’objet sous-jacent à l’exception du nom de l’objet sur lequel l’action est effectuée. Par exemple, l’action du message pour le **sélectionnez** sur une table dans le schéma SCOTT est : `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/[TABLE_NAME]/Select`. Si vous effectuez une opération Select sur un synonyme pour la même table dans le schéma SCOTT, l’action du message est : `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/[SYNONYM_NAME]/Select`.  
  
 Lorsque vous appelez une opération sur un synonyme dans l’adaptateur, l’adaptateur appelle le synonyme dans la base de données Oracle pour exécuter l’opération. Toutefois, l’adaptateur utilise le nom d’objet sous-jacent dans la définition du synonyme pour extraire les métadonnées.  
  
 Synonymes peuvent être utilisés dans les opérations normales sortantes, des opérations composites et d’interrogation.  
  
> [!NOTE]
>  Vous pouvez rechercher les synonymes dans [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] comme d’autres objets. Toutefois, vous ne peut pas rechercher des procédures dans des packages de synonyme à partir d’un nœud de niveau comme vous pouvez le faire pour les procédures à l’intérieur des packages. Pour plus d’informations sur la recherche pour les opérations dans l’adaptateur, consultez [Parcourir, rechercher et d’obtenir les métadonnées pour les opérations de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/browse-search-and-get-metadata-for-oracle-database-operations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)
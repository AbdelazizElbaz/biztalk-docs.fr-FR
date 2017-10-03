---
title: "Types de données de base SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f744fe14-4134-486d-b060-9ac2d5f21c56
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8e60816dc362fc4630e263397048bcdee8d774b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="basic-sql-server-data-types"></a>Types de données de base de SQL Server
Cette rubrique décrit comment les [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]met en évidence des types de données de base SQL Server.  
  
## <a name="supported-sql-server-data-types"></a>Types de données SQL Server pris en charge  
 Le tableau suivant montre comment les types de données SQL Server sont signalées par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:  
  
|Type de données de SQL Server|Type XSD|Type .NET|Commentaires|  
|--------------------------|--------------|---------------|--------------|  
|Bigint|Long|Long|-|  
|Binaire|Base64Binary|Byte[]|-|  
|bit|Booléen|Bool|-|  
|Char|Chaîne|Chaîne|-|  
|Date|DateTime|DateTime|-|  
|DateTime|DateTime|DateTime|Lors de l’écriture des données à un champ de date/heure, l’adaptateur stocke toujours l’heure GMT. Si vous spécifiez les informations de fuseau horaire, l’adaptateur utilise ces informations pour convertir la valeur en une valeur d’heure GMT valide et l’écrit dans la table de base de données. Par exemple, 12/31/2008T23:59:59 + 5:30 est écrite dans la table comme 31/12/2008 6:29:59 PM.<br /><br /> Toutefois, si vous ne spécifiez pas les informations de fuseau horaire, l’adaptateur considère que la valeur soit déjà au format GMT et écrit la même valeur dans la table. Par exemple, 12/31/2008T23:59:59 est écrite dans la table comme 31/12/2008 11:59:59 PM.|  
|Datetime2|DateTime|DateTime|-|  
|Datetimeoffset|DateTime|DateTime|-|  
|Décimal|XSD : decimal si la précision < = 28<br /><br /> XSD : String si la précision de 28 >|Décimal si la précision < = 28<br /><br /> Si la précision de la chaîne de 28 >|-|  
|Filestream|Base64Binary|Byte[]|-|  
|Float|Double|Double|-|  
|Géographie|Chaîne|Chaîne|-|  
|Géométrie|Chaîne|Chaîne|-|  
|Hierarchyid|Chaîne|Chaîne|-|  
|Image|Base64Binary|Byte[]|-|  
|int|int|int|-|  
|Money|Décimal|Décimal|-|  
|Nchar|Chaîne|Chaîne|-|  
|Ntext|Chaîne|Chaîne|-|  
|Numérique|Décimal|Décimal|-|  
|nvarchar|Chaîne|Chaîne|-|  
|Nvarchar (max)|Chaîne|Chaîne|-|  
|Real|Float|Float|-|  
|Smalldatetime|DateTime|DateTime|-|  
|Smallint|Short|Short|-|  
|Smallmoney|Décimal|Décimal|-|  
|SQLVariant|Chaîne|Chaîne|-|  
|Texte|Chaîne|Chaîne|-|  
|Time|Duration|intervalle de temps|-|  
|Horodateur|Base64Binary|Byte[]|-|  
|Tinyint|UnsignedByte|Byte|-|  
|Uniqueidentifier|{http://schemas.microsoft.com/2003/10/Serialization/} : guid|Guid|-|  
|Varbinary|Base64Binary|Byte[]|-|  
|Varbinary (max)|Base64Binary|Byte[]|-|  
|Varchar|Chaîne|Chaîne|-|  
|Varchar (max)|Chaîne|String|-|  
|XML|String|Chaîne|-|  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)
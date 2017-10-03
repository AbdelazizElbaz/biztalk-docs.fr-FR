---
title: "Limitations de l’adaptateur BizTalk pour SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a19b109-a6b7-452f-a544-48627fa52f36
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5a80990a9e3f417b64a06d8823300d53b2c4f3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="limitations-of-biztalk-adapter-for-sql-server"></a>Limitations de l’adaptateur BizTalk pour SQL Server
Les éléments suivants sont connus limitations pour [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]:  
  
-   Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ne prend pas en charge les synonymes créés dans la base de données SQL Server. Pour plus d’informations sur les synonymes dans SQL Server, consultez [http://go.microsoft.com/fwlink/?LinkId=120111](http://go.microsoft.com/fwlink/?LinkId=120111).  
  
-   Si vous modifiez l’heure système de l’ordinateur qui exécute le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] hôte, l’heure n’est pas actualisé automatiquement dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] hôte. Cela peut entraîner un comportement incorrect des opérations entrantes qui utilisent le port de réception de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour résoudre ce problème, vous devez redémarrer l’instance d’hôte qui possède un port de réception après avoir modifié l’heure système de l’ordinateur exécutant.  
  
-   Si un nom de paramètre dans une procédure stockée contient moins de 127 caractères, vous ne pouvez pas exécuter la procédure stockée à l’aide du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Il s’agit en raison de la limitation d’ADO.NET.  
  
-   Le WSDL le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] génère, lorsque converti en un proxy, expose la colonne DateTimeOffset en tant que System.DateTime. Ce type de données ne peut pas stocker les informations de fuseau horaire. Par conséquent, toute valeur de date/heure que l’adaptateur envoie au proxy sera convertie en heure locale de l’application .NET. Si vous souhaitez conserver les informations de fuseau horaire, vous devez modifier l’interface de votre proxy à utiliser le type de chaîne au lieu de System.DateTime. Ensuite, utilisez XmlConvert.ToDateTimeOffset pour créer un objet Sytstem.DateTimeOffset, qui peut stocker les informations de fuseau horaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)
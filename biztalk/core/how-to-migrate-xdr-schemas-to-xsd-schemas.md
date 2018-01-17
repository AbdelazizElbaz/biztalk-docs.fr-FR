---
title: "Comment migrer les schémas XDR vers des schémas XSD | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90bde0d0-bfe6-4d6c-823c-8ed9c0e15783
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84bbc42297a10c7d42adb8d778ba19b3b392742c
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-migrate-xdr-schemas-to-xsd-schemas"></a>Migration des schémas XDR vers des schémas XSD
Si vous migrez des schémas à partir d'une version précédente de BizTalk Server, vous devrez convertir vos schémas XDR (XML-Data Reduced) en des schémas de langage XSD (XML Schema Definition). Cette rubrique décrit les étapes nécessaires à cette migration.  
  
### <a name="to-generate-an-xsd-schema-from-an-xdr-schema"></a>Pour générer un schéma XSD à partir d'un schéma XDR  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le projet BizTalk approprié, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés - \< *BizTalk ProjectName* \>**  boîte de dialogue le **modèles** , cliquez sur **générer Schémas**, puis cliquez sur **ajouter**.  
  
3.  Dans le **générer les schémas** boîte de dialogue le **type de Document** liste, sélectionnez **schéma XDR**.  
  
4.  Cliquez sur **Parcourir**, recherchez le fichier de schéma XDR que vous souhaitez migrer, puis cliquez sur **OK**.  
  
     Un nouveau schéma est généré à partir du fichier de schéma XDR spécifié. Il porte le même nom que ce fichier ainsi que l'extension .xsd et est ensuite ouvert dans l'Éditeur BizTalk.  
  
> [!NOTE]
>  Évitez d'utiliser les mots réservés C# et les noms de type et d'espace de noms .NET Framework (tels que Système) en tant que noms de nœud racine de schéma ou que noms de fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des schémas dans des projets](../core/managing-schemas-within-projects.md)   
 [Migration des enregistrements de fichier plat](../core/migrating-flat-file-records.md)
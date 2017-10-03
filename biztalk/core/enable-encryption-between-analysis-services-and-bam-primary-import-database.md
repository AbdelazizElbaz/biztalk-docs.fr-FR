---
title: "Comment activer le chiffrement entre Analysis Services et la base de données importation principale BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Analysis Services, enabling encryption
- Primary Import database [BAM], SQL Server Analysis Services
- Primary Import database [BAM], enabling encryption
- SQL Server Analysis Services, Primary Import database [BAM]
ms.assetid: 8107c557-e57c-4569-9ff7-abcb7a8e5243
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77069c3690a73957936c786bc05c2690b9df7a10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-encryption-between-analysis-services-and-the-bam-primary-import-database"></a>Activation du chiffrement entre Analysis Services et la base de données d'importation principale BAM
Durant l'installation ou la mise à niveau de l'analyse BAM, le chiffrement n'est pas activé par défaut. Pour activer le chiffrement, vous devez définir l'indicateur UseEncryption du fichier XML de configuration BAM sur la valeur 1.  
  
 Vous devez aussi activer le chiffrement dans SQL Server Analysis Services. Pour plus d’informations sur l’activation du chiffrement, consultez [sécurisation des communications Client avec une Instance Analysis Services](http://go.microsoft.com/fwlink/?LinkId=190805) (http://go.microsoft.com/fwlink/?LinkId=190805).  
  
### <a name="to-enable-encryption-between-sql-server-analysis-services-and-the-bam-primary-import-database"></a>Pour activer le chiffrement entre SQL Server Analysis Services et la base de données d'importation principale BAM  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].  
  
3.  Type **bm get-config - FileName :\<fichier de sortie >**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
4.  Appuyez sur **Entrée**.  
  
5.  Ouvrez le fichier de configuration de fichier que vous avez exporté dans un éditeur de texte, puis définissez la valeur de l'indicateur de propriété UseEncryption sur 1.  
  
    -   Paramètre par défaut : \<nom de la propriété = « UseEncryption » > 0\<cette propriété >  
  
    -   Nouveau paramètre : \<nom de la propriété = « UseEncryption » > 1\<cette propriété >  
  
6.  Mettre à jour la configuration BAM en tapant **bm update-config - FileName :\<le fichier de configuration >**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)
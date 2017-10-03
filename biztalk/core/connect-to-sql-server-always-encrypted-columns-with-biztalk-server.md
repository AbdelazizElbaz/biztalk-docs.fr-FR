---
title: "Se connecter à SQL Server Always Encrypted des colonnes avec BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fcc20a2b-daf9-4b7f-ae61-cb408e4bd04c
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 62b570fabda6a0e46f87c36b863e2b99e464020b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-sql-server-always-encrypted-columns-with-biztalk-server"></a>Se connecter à SQL Server Always Encrypted des colonnes avec BizTalk Server
Activer le chiffrement intégral dans l’adaptateur WCF-SQL dans [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] pour interroger des colonnes chiffrées.  

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , l’adaptateur WCF-SQL peut interroger des colonnes chiffrées dans [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)]. Le `ColumnEncryptionSetting` propriété de liaison est utilisée pour activer ou désactiver la fonctionnalité pour obtenir les valeurs de déchiffrés/chiffré de colonne à partir d’une base de données Always Encrypted.

Cette rubrique vous indique comment activer ou désactiver cette fonctionnalité dans [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].

> [!TIP] 
> [Always Encrypted (moteur de base de données)](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) est un bon point de départ pour comprendre et en savoir plus sur cette [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)] fonctionnalité.

## <a name="prerequisites"></a>Conditions préalables
Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].

## <a name="enable-always-encrypted"></a>Activer Always Encrypted

1. Dans le **Administration de BizTalk Server** de la console, cliquez sur le port WCF-SQL, puis sélectionnez **propriétés**.
2. Accédez à la **liaison** onglet.
3. Sous **Always Encrypted**, activez ou désactivez le `ColumnEncryptionSettings` propriété :

* **Activé**: les requêtes de port et obtient les données chiffrées à partir d’une base de données Always Encrypted
* **Désactivé**: le port interroge la base de données Always Encrypted, mais les données retournées est haché

    ![Activer Always Encrypted](../core/media/enable-always-encrypted.png)

4. Sélectionnez **appliquer**, et **OK** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi
[Always Encrypted (moteur de base de données)](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine)  
[Configurer le Pack de fonctionnalités](../core/configure-the-feature-pack.md)
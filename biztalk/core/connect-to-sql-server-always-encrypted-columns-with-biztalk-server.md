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
# <a name="connect-to-sql-server-always-encrypted-columns-with-biztalk-server"></a><span data-ttu-id="cb397-102">Se connecter à SQL Server Always Encrypted des colonnes avec BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cb397-102">Connect to SQL Server Always Encrypted columns with BizTalk Server</span></span>
<span data-ttu-id="cb397-103">Activer le chiffrement intégral dans l’adaptateur WCF-SQL dans [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] pour interroger des colonnes chiffrées.</span><span class="sxs-lookup"><span data-stu-id="cb397-103">Enable Always Encrypted in the WCF-SQL adapter in [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] to query encrypted columns.</span></span>  

<span data-ttu-id="cb397-104">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , l’adaptateur WCF-SQL peut interroger des colonnes chiffrées dans [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb397-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, the WCF-SQL adapter can query encrypted columns in [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="cb397-105">Le `ColumnEncryptionSetting` propriété de liaison est utilisée pour activer ou désactiver la fonctionnalité pour obtenir les valeurs de déchiffrés/chiffré de colonne à partir d’une base de données Always Encrypted.</span><span class="sxs-lookup"><span data-stu-id="cb397-105">The `ColumnEncryptionSetting` binding property is used to enable or disable the functionality to get decrypted/encrypted column values from an Always Encrypted database.</span></span>

<span data-ttu-id="cb397-106">Cette rubrique vous indique comment activer ou désactiver cette fonctionnalité dans [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb397-106">This topic shows you how to enable or disable this feature in [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span>

> [!TIP] 
> <span data-ttu-id="cb397-107">[Always Encrypted (moteur de base de données)](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) est un bon point de départ pour comprendre et en savoir plus sur cette [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)] fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="cb397-107">[Always Encrypted (Database Engine)](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) is a great resource to understand and learn more about this [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)] feature.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cb397-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="cb397-108">Prerequisites</span></span>
<span data-ttu-id="cb397-109">Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb397-109">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span>

## <a name="enable-always-encrypted"></a><span data-ttu-id="cb397-110">Activer Always Encrypted</span><span class="sxs-lookup"><span data-stu-id="cb397-110">Enable Always Encrypted</span></span>

1. <span data-ttu-id="cb397-111">Dans le **Administration de BizTalk Server** de la console, cliquez sur le port WCF-SQL, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="cb397-111">In the **BizTalk Server Administration** console, right-click your WCF-SQL port, and select **Properties**.</span></span>
2. <span data-ttu-id="cb397-112">Accédez à la **liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="cb397-112">Go to the **Binding** tab.</span></span>
3. <span data-ttu-id="cb397-113">Sous **Always Encrypted**, activez ou désactivez le `ColumnEncryptionSettings` propriété :</span><span class="sxs-lookup"><span data-stu-id="cb397-113">Under **Always Encrypted**, enable or disable the `ColumnEncryptionSettings` property:</span></span>

* <span data-ttu-id="cb397-114">**Activé**: les requêtes de port et obtient les données chiffrées à partir d’une base de données Always Encrypted</span><span class="sxs-lookup"><span data-stu-id="cb397-114">**Enabled**: The port queries, and gets encrypted data from an Always Encrypted database</span></span>
* <span data-ttu-id="cb397-115">**Désactivé**: le port interroge la base de données Always Encrypted, mais les données retournées est haché</span><span class="sxs-lookup"><span data-stu-id="cb397-115">**Disabled**: The port queries the Always Encrypted database, but the data returned is hashed</span></span>

    ![Activer Always Encrypted](../core/media/enable-always-encrypted.png)

4. <span data-ttu-id="cb397-117">Sélectionnez **appliquer**, et **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="cb397-117">Select **Apply**, and **OK** to save your changes.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb397-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb397-118">See also</span></span>
[<span data-ttu-id="cb397-119">Always Encrypted (moteur de base de données)</span><span class="sxs-lookup"><span data-stu-id="cb397-119">Always Encrypted (Database Engine)</span></span>](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine)  
[<span data-ttu-id="cb397-120">Configurer le Pack de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="cb397-120">Configure the Feature Pack</span></span>](../core/configure-the-feature-pack.md)
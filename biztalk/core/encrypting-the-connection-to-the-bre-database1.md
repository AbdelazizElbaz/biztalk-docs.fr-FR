---
title: "Chiffrement de la connexion à la Database1 BRE | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63edd2bb-97f1-4b8b-8cdc-f4792909ca86
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0dd585c596f7635417a4e22cbccda04593e7c598
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="encrypting-the-connection-to-the-bre-database"></a>Chiffrement de la connexion à la base de données BRE
En fonction de la stratégie de sécurité de votre entreprise, envisagez le chiffrement des éléments suivants :  
  
-   informations d'identification transmises lors de l'ouverture de session ;  
  
-   données transmises sur un réseau entre l'ordinateur client sur lequel est exécutée la stratégie du moteur des règles d'entreprise (BRE) et la base de données du moteur de règles.  
  
 Cette rubrique décrit le chiffrement des connexions aux bases de données BRE hébergées sur un serveur [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] ou [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)].  
  
## <a name="to-encrypt-the-connection-to-the-bre-database-hosted-on-sql-server-2008-sp1-or-sql-server-2008-r2"></a>Pour chiffrer la connexion à la base de données BRE hébergée sur un serveur SQL Server 2008 SP1 ou SQL Server 2008 R2  
 Par défaut, les informations d'identification transmises lors de la connexion d'une application cliente à un serveur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sont chiffrées. Si aucun certificat n'est présent sur le serveur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], celui-ci génère, au démarrage, un certificat auto-signé qui servira au chiffrement des paquets de connexion.  
  
 Pour activer le chiffrement des données transmises sur un réseau entre [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et le client d’une instance de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], vous devez définir le **forcer le chiffrement** option sur le serveur à **Oui**ou définir le **forcer le chiffrement du protocole** option **Oui** sur le client.  
  
 Lorsque le **forcer le chiffrement** option est définie sur **Oui** côté serveur, [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] utilise SSL pour chiffrer toutes les communications *entre tous les clients et le serveur de base de données*. En d'autres termes, toutes les connexions entrantes côté serveur sont chiffrées. Pour activer cette option sur le serveur, nous vous recommandons d'installer un certificat sur le serveur à l'aide du Gestionnaire de configuration SQL Server. Si aucun certificat n'est installé sur le serveur, ce dernier génère automatiquement un certificat auto-signé lors du démarrage de l'instance.  
  
 Ce certificat auto-signé peut être utilisé en remplacement d'un certificat émanant d'une autorité de certification approuvée, mais il ne fournit aucune protection contre une éventuelle usurpation d'identité. Ne faites jamais confiance à une connexion SSL utilisant des certificats autosignés dans un environnement de production ou sur des serveurs connectés à Internet. Une fois cette option activée, l'accès est refusé à tout client ne prenant pas en charge le chiffrement. SQL Server doit être redémarré après avoir défini la **forcer le chiffrement** option. Pour définir cette option, vous pouvez utiliser le Gestionnaire de configuration SQL Server (Configuration réseau [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]).  
  
 Lorsque le **forcer le chiffrement du protocole** est définie sur le côté client, [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] utilise SSL pour chiffrer toutes les communications *entre le client et tous les serveurs*. En d'autres termes, toutes les connexions sortantes côté client sont chiffrées. Pour activer cette option sur le côté client, vous devez installer un certificat sur le serveur si la **faire confiance au certificat serveur** option sur le client est définie sur **non**. Si le **faire confiance au certificat serveur** option sur le client est définie sur **Oui**, le client ne valide pas le certificat de serveur, ce qui permet l’utilisation d’un certificat auto-signé. Pour définir cette option, vous pouvez utiliser le Gestionnaire de configuration SQL Server (Configuration de SQL Native Client).  
  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]également vous permet d’activer le chiffrement pour un *connexion spécifique à partir d’un client au serveur* en définissant le **chiffrer/utiliser le chiffrement des données** indicateur **Oui** dans le chaîne de connexion. Toutefois, le moteur BRE génère automatiquement les chaînes de connexion sans définir l’option de chiffrement sur **Oui**. Par conséquent, vous ne pouvez pas chiffrer de connexion au serveur de la base de données du moteur de règles depuis l'ordinateur client. Au lieu de cela, vous devez définir le **forcer le chiffrement du protocole** option sur le client, comme indiqué dans le paragraphe précédent.
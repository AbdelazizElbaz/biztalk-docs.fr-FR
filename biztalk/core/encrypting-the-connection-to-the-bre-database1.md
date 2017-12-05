---
title: "Chiffrer la connexion de base de données BRE | Documents Microsoft"
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
ms.openlocfilehash: 1b3891ef72b5b1aeba42bce1586ee9c73aa29408
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="encrypt-the-connection-to-the-bre-database"></a>Chiffrer la connexion à la base de données BRE
En fonction de la stratégie de sécurité de votre entreprise, envisagez le chiffrement des éléments suivants :  
  
-   informations d'identification transmises lors de l'ouverture de session ;  
  
-   données transmises sur un réseau entre l'ordinateur client sur lequel est exécutée la stratégie du moteur des règles d'entreprise (BRE) et la base de données du moteur de règles.  
  
 Cette rubrique décrit comment chiffrer les connexions aux bases de données BRE hébergées sur SQL Server.  
  
## <a name="encrypt-the-connection-to-the-bre-database"></a>Chiffrer la connexion à la base de données BRE
 Par défaut, les informations d’identification qui sont transmises au cours du processus d’ouverture de session, lorsqu’une application cliente se connecte à SQL Server sont chiffrées. Si aucun certificat n'est présent sur le serveur SQL Server, celui-ci génère, au démarrage, un certificat auto-signé qui servira au chiffrement des paquets de connexion.  
  
 Pour activer le chiffrement des données transmises sur un réseau entre SQL Server et le client d’une instance de SQL Server, vous devez définir le **forcer le chiffrement** option sur le serveur à **Oui** ou définir le **Forcer le chiffrement du protocole** option **Oui** sur le client.  
  
 Lorsque le **forcer le chiffrement** option est définie sur **Oui** côté serveur, SQL Server utilise SSL pour chiffrer toutes les communications *entre tous les clients et le serveur de base de données* . En d'autres termes, toutes les connexions entrantes côté serveur sont chiffrées. Pour activer cette option sur le serveur, nous vous recommandons d'installer un certificat sur le serveur à l'aide du Gestionnaire de configuration SQL Server. Si aucun certificat n'est installé sur le serveur, ce dernier génère automatiquement un certificat auto-signé lors du démarrage de l'instance.  
  
 Ce certificat auto-signé peut être utilisé en remplacement d'un certificat émanant d'une autorité de certification approuvée, mais il ne fournit aucune protection contre une éventuelle usurpation d'identité. Ne faites jamais confiance à une connexion SSL utilisant des certificats autosignés dans un environnement de production ou sur des serveurs connectés à Internet. Une fois cette option activée, l'accès est refusé à tout client ne prenant pas en charge le chiffrement. SQL Server doit être redémarré après avoir défini la **forcer le chiffrement** option. Vous pouvez définir cette option en utilisant le Gestionnaire de Configuration SQL Server (Configuration du réseau SQL Server).  
  
 Lorsque le **forcer le chiffrement du protocole** est définie sur le côté client, SQL Server utilise SSL pour chiffrer toutes les communications *entre le client et tous les serveurs*. En d'autres termes, toutes les connexions sortantes côté client sont chiffrées. Pour activer cette option sur le côté client, vous devez installer un certificat sur le serveur si la **faire confiance au certificat serveur** option sur le client est définie sur **non**. Si le **faire confiance au certificat serveur** option sur le client est définie sur **Oui**, le client ne valide pas le certificat de serveur, ce qui permet l’utilisation d’un certificat auto-signé. Pour définir cette option, vous pouvez utiliser le Gestionnaire de configuration SQL Server (Configuration de SQL Native Client).  
  
 SQL Server vous permet également à activer le chiffrement d’un *connexion spécifique à partir d’un client au serveur* en définissant le **chiffrer/utiliser le chiffrement des données** indicateur **Oui** dans la chaîne de connexion. Toutefois, le moteur BRE génère automatiquement les chaînes de connexion sans définir l’option de chiffrement sur **Oui**. Par conséquent, vous ne pouvez pas chiffrer de connexion au serveur de la base de données du moteur de règles depuis l'ordinateur client. Au lieu de cela, vous devez définir le **forcer le chiffrement du protocole** option sur le client, comme indiqué dans le paragraphe précédent.
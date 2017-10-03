---
title: "Sécurité entre le système Siebel et l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, IPsec
- connection URI
- security considerations, between the Siebel system and the adapter
ms.assetid: 40b03d4e-f489-4dce-ba7b-6b6f394275ac
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb9ced17c00432039ff3b85ac85d56e1b6031049
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-between-the-siebel-system-and-the-adapter"></a>Sécurité entre le système Siebel et de la carte
## <a name="encryption-and-authentication"></a>Chiffrement et authentification
Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] peut prendre en charge le chiffrement rsa ou mscrypto sur les données qu’il échange avec le système Siebel. Vous configurez le mode de chiffrement via un paramètre de chaîne de requête dans l’URI de connexion. Pour plus d’informations sur l’URI de connexion Siebel, consultez [créer Siebel système connexion URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md). Pour plus d’informations sur le support de chiffrement rsa et mscrypto par Siebel, consultez la documentation de Siebel.  
  
 En spécifiant un mode de chiffrement peut aider à garantir la confidentialité des données échangées entre l’adaptateur et le système Siebel. Toutefois, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne fournit pas de mécanismes qui prennent en charge de l’intégrité des données, d’authentification ou d’autorisation sur ces échanges. Si ces problèmes sont un problème dans votre environnement, vous devez fournir un mécanisme de sécurité pour les atténuer.  
  
 Un mécanisme possible pour aider à fournir davantage de sécurité sur le réseau est la sécurité du protocole Internet (IPsec). IPsec est une infrastructure de normes ouvertes pour la protection des communications sur des réseaux IP (Internet Protocol). Pour plus d’informations sur IPsec et à l’aide d’IPsec avec les produits Microsoft, consultez l’article Microsoft TechNet « IPsec » à [http://go.microsoft.com/fwlink/?LinkID=196851](http://go.microsoft.com/fwlink/?LinkID=196851).  
  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] prend en charge d’authentification et autorisation sur les connexions qu’il établit avec le système Siebel via le nom du mot de passe informations d’identification utilisateur que vous fournissez. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] utilise ces informations d’identification pour authentifier l’utilisateur sur le système Siebel lorsqu’il ouvre une connexion. Ces informations d’identification fournissent un niveau d’autorisation sur le système Siebel pour la connexion. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] fournit un certain nombre de méthodes par le biais duquel vous pouvez fournir ces informations d’identification. Pour plus d’informations sur la façon de fournir en toute sécurité les informations d’identification de Siebel dans les solutions BizTalk, consultez [sécurité avec l’adaptateur Siebel et BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md). Pour plus d’informations sur la façon de fournir des informations d’identification du système Siebel dans les solutions de programmation en toute sécurité, consultez [programmation sécurisée avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/secure-programming-with-the-siebel-adapter.md).  
  
> [!NOTE]
>  Les informations d’identification utilisées par le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] pour établir une connexion à la Siebel système ne fournissent pas d’authentification au niveau du message ou au niveau du transport ou autorisation pour les données transitent par le réseau. Ils sont uniquement utilisés pour ouvrir une connexion et d’authentifier l’utilisateur sur le système Siebel.  
  
## <a name="see-also"></a>Voir aussi  
[Sécuriser vos applications Siebel](../../adapters-and-accelerators/adapter-siebel/secure-your-siebel-applications.md)
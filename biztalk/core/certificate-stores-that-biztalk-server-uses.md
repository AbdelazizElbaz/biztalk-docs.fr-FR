---
title: Magasins de certificats par BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- public key certificates
- certificate stores, warnings
- private key certificates
- certificates, private key
- Other People stores [certificates]
- certificate stores, Personal store
- Personal store [certificates]
- certificate stores, Windows stores
- certificates, public key
- certificates, certificate stores
- certificate stores
ms.assetid: 29b65913-be3b-45d9-9865-02e52e4370f4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b142ff5b9c9007a86b09acd25f53f8c88796988c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="certificate-stores-that-biztalk-server-uses"></a>Magasins de certificats utilisés par BizTalk Server
BizTalk Server utilise deux types de magasins de certificats : le magasin de certificats Autres personnes pour les clés publiques et le magasin de certificats Personnel pour chaque compte de service d'instance d'hôte pour la clé privée.  
  
 **Magasin de certificats autres personnes.** Comme leur nom l'indique, les certificats de clé publique sont publics et accessibles par tout individu ayant accès à l'ordinateur sur lequel ils sont stockés. BizTalk Server utilise des certificats de clé publique pour chiffrer des messages destinés à des tiers spécifiques et pour vérifier les signatures numériques des messages entrants envoyés par des tiers spécifiques. Windows fournit le magasin de certificats Autres personnes pour stocker les certificats de clé publique utilisés sur l'ordinateur. Tous les utilisateurs peuvent lire et utiliser les certificats de ce magasin et les administrateurs Windows ont les autorisations pour maintenir ce magasin.  
  
> [!NOTE]
>  Vous devez enregistrer les certificats de clé publique sur le magasin de certificats Ordinateur local\Autres personnes de l'ordinateur local sur lequel se trouve une instance d'hôte BizTalk utilisée pour vérifier la signature ou chiffrer les messages envoyés à un partenaire distant.  
  
 La figure suivante montre le magasin de certificats Autres personnes utilisé par BizTalk Server pour les certificats de clé publique :  
  
 ![Magasin de certificats d’autres personnes](../core/media/bpi-sp-msgsec-otherpeoplecertstore.gif "BPI_SP_MSGSEC_OTHERPEOPLECERTSTORE")  
  
 **Magasin de certificats personnel.** BizTalk Server utilise des certificats de clé privée pour déchiffrer les messages entrants et signer les messages sortants. Chaque compte Windows configuré pour se connecter de manière interactive à un ordinateur possède un magasin de certificats personnels destinés au système d'exploitation. Il est le seul à pouvoir accéder à ce magasin. BizTalk Server utilise les magasins de certificats personnels pour chaque compte de service d'instance d'hôte afin d'accéder aux certificats de clé privée auxquels chaque compte de service a accès. Seuls les propriétaires du magasin de certificats peuvent accéder à et maintenir leurs magasins de certificats personnels. En d'autres termes, vous devez vous connecter à chaque ordinateur qui héberge des pipelines de décodage S/MIME comme chaque compte de service d'hôte, puis importer le certificat de déchiffrement dans le magasin de certificats personnel à l'aide du composant logiciel enfichable Certificats.  
  
 La figure suivante montre le magasin de certificats Personnel utilisé par BizTalk Server pour les certificats de clé privée :  
  
 ![Magasin de certificats de l’utilisateur actuel](../core/media/bpi-sp-msgsec-mystore.gif "BPI_SP_MSGSEC_MYSTORE")  
  
> [!IMPORTANT]
>  Les certificats de clé privée doivent être stockés dans le magasin de certificats Utilisateur actuel\Personnel pour chaque compte de service d'instance d'hôte sur chaque ordinateur disposant d'une instance d'hôte BizTalk en cours d'exécution qui requiert le certificat de déchiffrement ou de signature des messages sortants.  
  
> [!NOTE]
>  Une fois que vous avez ajouté le certificat avec la clé privée au magasin de certificats personnel des comptes de service qui signe les messages sortants, vous devez également spécifier ce certificat de signature dans la console Administration de BizTalk. Pour plus d’informations, consultez [comment configurer BizTalk Server pour l’envoi de Messages signés](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md).  
  
> [!NOTE]
>  Le magasin de certificats personnel est également appelé Mon magasin de certificats lorsqu'il est utilisé pour des opérations de programmation, telles que le script de l'importation et de l'exportation de certificats.  
  
 Le tableau suivant décrit les certificats que vous devez installer dans chaque magasin de certificats Windows.  
  
### <a name="table-1-certificates-for-each-windows-certificate-store"></a>Tableau 1 Certificats pour chaque magasin de certificats Windows  
  
|**Objectif du certificat**|**Type de certificat**|**Magasin de certificats**|  
|-----------------------------|--------------------------|---------------------------|  
|La signature|Clé privée personnelle|Magasin personnel pour chaque compte de service d’une instance d’hôte qui a un pipeline d’envoi avec un composant de pipeline Encodeur MIME/SMIME configuré pour signer des messages (**ajouter un certificat de signature au Message** propriété `True`). Pour plus d’informations, consultez [comment configurer BizTalk Server pour l’envoi de Messages signés](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md)|  
|Vérification de signature|Clé privée du partenaire|Magasin Autres personnes sur chaque ordinateur qui a une instance d'hôte avec un pipeline de réception doté d'un composant de pipeline Décodeur MIME/SMIME. Pour plus d’informations, consultez [comment configurer BizTalk Server pour la réception de Messages signés](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md).|  
|Déchiffrement|Clé privée personnelle|Magasin Personnel pour chaque compte de service d'une instance d'hôte qui a un pipeline de réception doté d'un composant de pipeline Décodeur MIME/SMIME. Pour plus d’informations, consultez [comment configurer BizTalk Server pour recevoir des Messages chiffrés](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md).|  
|Le chiffrement|Clé privée du partenaire|Magasin autres personnes sur chaque ordinateur qui possède une instance d’hôte qui a un pipeline d’envoi avec un composant de pipeline Encodeur MIME/SMIME configuré pour chiffrer les messages (**activer le chiffrement** propriété `True)`. Pour plus d’informations, consultez [comment configurer BizTalk Server pour envoyer des Messages chiffrés](../core/how-to-configure-biztalk-server-for-sending-encrypted-messages.md).|  
|Résolution du tiers|Clé privée du partenaire|Magasin Autres personnes sur l'ordinateur d'administration à partir duquel vous configurez la résolution de tiers. Pour plus d’informations, consultez [à l’aide de certificats pour la résolution de tiers](../core/using-certificates-for-party-resolution.md).|  
  
 La figure suivante présente les certificats nécessaires dans chaque magasin de certificats sur BizTalk Server dédié à la réception de messages.  
  
 ![Certificats requis pour recevoir des messages sécurisés](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")  
  
 La figure suivante présente les certificats nécessaires dans chaque magasin de certificats sur BizTalk Server dédié à l'envoi de messages.  
  
 ![Certificats requis pour envoyer des messages sécurisés](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")  
  
 Pour plus d'informations sur les magasins de certificats et le composant logiciel enfichable Certificats pour la console MMC (Microsoft Management Console), recherchez « console Certificats » dans l'aide de Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Certificats utilisés par BizTalk Server pour les Messages signés](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)   
 [Certificats utilisés par BizTalk Server pour les Messages chiffrés](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md)   
 [Chiffrement et les certificats de signature](../core/encryption-and-signing-certificates.md)   
 [Implémentation de la sécurité de Message](../core/implementing-message-security.md)
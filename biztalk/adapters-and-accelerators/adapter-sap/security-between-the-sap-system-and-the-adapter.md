---
title: "Sécurité entre le système SAP et la carte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Secure Network Communications
- SNC
- security, user name password credentials
- security, for inbound scenarios
- security considerations, between SAP system and adapter
- user name password credentials
ms.assetid: fa21df0b-a364-4a52-8c38-49c5ee6267cc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1c0e37662b9c554d05b73ecf234da4b2ee547fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-between-the-sap-system-and-the-adapter"></a>Sécurité entre le système SAP et de l’adaptateur
Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] prend en charge les Communications SAP du réseau sécurisée (SNC) ou utilisateur nom mot de passe pour aider à sécuriser la communication entre elle et le serveur SAP. Informations d’identification de mot de passe utilisateur fournissent uniquement une autorisation pour la connexion au système SAP ; ils ne fournissent pas toute la sécurité sur les données échangées sur la connexion. Vous ne pouvez pas utiliser les informations d’identification mot de passe de nom SNC et utilisateur simultanément.  
  
## <a name="sap-secure-network-communications"></a>SAP sécuriser les Communications réseau  
 Communication réseau sécurisée (SNC) est une couche de l’architecture du système SAP qui fournit une sécurité au niveau de l’application sur les données échangées entre le client SAP et un serveur d’applications SAP.  
  
 SNC offre les avantages suivants :  
  
-   SNC cible au niveau de l’application, de bout en bout pour la sécurité. SNC permet de sécuriser toutes les communications entre deux composants SNC protégé (par exemple, entre l’interface utilisateur graphique SAP et un serveur d’applications SAP système).  
  
-   Vous pouvez implémenter des fonctionnalités de sécurité supplémentaires que le système SAP ne fournit pas directement (par exemple, l’authentification unique ou l’utilisation de cartes à puce pour l’authentification).  
  
-   Vous pouvez personnaliser votre implémentation SNC. Vous pouvez utiliser le produit de sécurité de votre choix et choisissez les algorithmes que vous souhaitez utiliser.  
  
-   Vous pouvez modifier le produit de sécurité à tout moment sans affecter les applications d’entreprise système SAP.  
  
 Pour utiliser SNC, vous devez configurer le serveur SAP et le client qui exécute le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
-   Configurer les Communications de réseau sécurisée (SNC) sur le serveur SAP. Consultez la documentation SAP pour obtenir des conseils.  
  
-   Sur l’ordinateur de la DLL du client SAP et [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] installé, vous devez également le SNC aux fichiers DLL associés. Pour plus d’informations sur ces DLL, consultez le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] [les composants logiciels requis](../../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md).  
  
-   Pour configurer l’adaptateur pour utiliser SNC, vous devez définir le paramètre UseSnc dans l’URI de connexion SAP. Pour plus d’informations sur l’URI de connexion SAP, consultez [configurer l’URI de connexion pour l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/configure-the-connection-uri-for-the-sap-adapter.md). En outre, vous devez définir le **SncLibrary** et **SncPartnerName** propriétés de liaison. Pour plus d’informations sur la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
## <a name="user-name-password-credentials"></a>Informations d’identification de mot de passe utilisateur  
 Vous pouvez fournir des informations d’identification de mot de passe de nom utilisateur à l’adaptateur dans l’URI de connexion. L’adaptateur utilise ces informations d’identification pour authentifier l’utilisateur sur le système SAP lorsqu’il ouvre la connexion. Ces informations d’identification fournissent un niveau d’autorisation pour la connexion au système SAP ; Toutefois, elles ne fournissent pas au niveau du message ou au niveau du transport authentification (ou autorisation) pour les données transitant par le réseau.  
  
 Pour cette raison, vous devez fournir un mécanisme de sécurité pour garantir des niveaux d’autorisation, d’authentification, de confidentialité des données et de l’intégrité des données pour les échanges de données entre l’adaptateur et le système SAP.  
  
> [!IMPORTANT]
>  Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces le **AcceptCredentialsInUri** propriété de liaison. Cette propriété détermine si les informations d’identification du système SAP sont autorisées dans l’URI de connexion. Par défaut, **AcceptCredentialsInUri** a la valeur false et le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] lève une exception si les informations d’identification sont incluses dans l’URI. Pour plus d’informations, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
 Un mécanisme possible pour aider à fournir davantage de sécurité sur le réseau est la sécurité du protocole Internet (IPsec). IPsec est une infrastructure de normes ouvertes pour la protection des communications sur des réseaux IP (Internet Protocol).  
  
 Le nom d’utilisateur et un mot de passe sont spécifiés en texte clair dans l’URI de connexion. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] fournit un certain nombre de méthodes par le biais duquel vous pouvez en toute sécurité fournir ces informations d’identification.  
  
-   Pour plus d’informations sur la façon de fournir des informations d’identification du système SAP dans les solutions BizTalk en toute sécurité, consultez [sécurité avec l’adaptateur SAP et de BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).  
  
-   Pour plus d’informations sur la façon de fournir des informations d’identification du système SAP dans les solutions de programmation en toute sécurité, consultez [programmation sécurisée avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/secure-programming-with-the-sap-adapter.md).  
  
## <a name="security-concerns-for-inbound-scenarios"></a>Problèmes de sécurité pour les scénarios de trafic entrants  
 N’importe quel écouteur qui a accès à un ID de programme SAP risque de recevoir tous les artefacts SAP (RFC IDOC et tRFCs) envoyées à cet ID de programme. Si plus d’un écouteur est inscrit pour l’ID de programme, SAP attribuera aléatoirement les artefacts qui arrivent à cet ID de programme pour un des écouteurs. Vous devez, par conséquent, vous assurer que seuls les écouteurs que vous souhaitez recevoir des messages à l’aide d’un ID de programme spécifique ont accès à cet ID de programme. En outre, étant donné que SAP envoie au hasard des artefacts dans les écouteurs d’attaché à un ID de programme, il est recommandé de dédier un ID de programme à un seul écouteur.  
  
## <a name="see-also"></a>Voir aussi  
[Meilleures pratiques pour sécuriser l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md)  
[Sécuriser vos applications SAP](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)
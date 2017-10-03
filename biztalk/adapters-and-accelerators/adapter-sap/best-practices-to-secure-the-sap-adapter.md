---
title: "Meilleures pratiques pour sécuriser l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security, best practices
ms.assetid: e60014b5-ce2f-4fd4-be2a-921d5cd81267
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34d6c56af06bb6b8dc0831c354d494bb62ad5bfa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-to-secure-the-sap-adapter"></a>Meilleures pratiques pour sécuriser l’adaptateur SAP
Cette section présente les meilleures pratiques à suivre pour protéger plus complètement les données sensibles lorsque vous utilisez ou développerez des applications qui consomment le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].  
  
## <a name="security-best-practices-for-the-connection-between-the-sap-adapter-and-the-sap-system"></a>Meilleures pratiques de sécurité pour la connexion entre l’adaptateur SAP et le système SAP  
  
-   Vous devez vous assurer un niveau adéquat de sécurité pour les données échangées entre l’adaptateur et le système SAP. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge les Communications de réseau sécurisée (SNC) SAP. Vous pouvez activer SNC ou fournir un autre mécanisme pour aider à sécuriser la communication entre l’adaptateur et le système SAP.  
  
-   Ne fournissez pas les informations d’identification de mot de passe utilisateur pour le système SAP dans l’URI de connexion. Consultez les sections suivantes pour les autres méthodes permettent de fournir des informations d’identification pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
-   Assurez-vous que les écouteurs uniquement que vous souhaitez recevoir les artefacts SAP (RFC IDOC et tRFCs) à partir d’un ID de programme SAP ont accès à cet ID de programme. C’est parce que n’importe quel écouteur qui a accès à un ID de programme peut recevoir des artefacts à partir de cet ID de programme.  
  
-   N’oubliez pas que si plusieurs écouteurs utilisez simultanément un ID de programme SAP, SAP choisit de manière aléatoire un écouteur pour chaque artefact sortant (RFC, IDOC ou tRFC).  
  
 Pour plus d’informations, consultez [sécurité entre le système SAP et la carte](../../adapters-and-accelerators/adapter-sap/security-between-the-sap-system-and-the-adapter.md).
  
## <a name="security-best-practices-for-consuming-the-sap-adapter-with-biztalk-server"></a>Meilleures pratiques de sécurité pour l’utilisation de l’adaptateur SAP avec BizTalk Server  
  
-   Ne fournissez pas les informations d’identification de mot de passe utilisateur pour le système SAP dans l’URI de connexion.  
  
-   Lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], entrez les informations d’identification de mot de passe de nom utilisateur pour le système SAP à partir de la **sécurité** onglet de la **configurer l’adaptateur** boîte de dialogue.  
  
-   Lorsque vous configurez l’adaptateur BizTalk WCF-Custom pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] sur un port d’envoi, entrez les informations d’identification de mot de passe de nom utilisateur pour le système SAP à partir de la **informations d’identification** onglet du **configurer Transport personnalisé WCF** boîte de dialogue.  
  
-   Lorsque vous configurez l’adaptateur BizTalk WCF-Custom pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] sur un emplacement de réception, entrez les informations d’identification de mot de passe de nom utilisateur pour le système SAP à partir de la **autres** onglet du **configurer Transport personnalisé WCF** boîte de dialogue.  
  
 Pour plus d’informations, consultez [sécurité avec l’adaptateur SAP et de BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).
  
## <a name="security-best-practices-for-consuming-the-sap-adapter-with-programming-solutions"></a>Meilleures pratiques de sécurité pour l’utilisation de l’adaptateur SAP avec les Solutions de programmation  
  
-   Il est parfois nécessaire de fournir des informations d’identification de mot de passe de l’utilisateur pour le système SAP dans l’URI ; de connexion Toutefois, si possible, vous devez éviter cette opération.  
  
-   Lorsque vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], entrez les informations d’identification de mot de passe de nom utilisateur pour le système SAP à partir de la **sécurité** onglet de la **configurer l’adaptateur** boîte de dialogue.  
  
-   Dans la programmation du modèle de canal WCF, vous devez utiliser le **informations d’identification** propriété sur la fabrication de canal pour définir les informations d’identification de mot de passe nom utilisateur pour le système SAP.  
  
-   Dans la programmation du modèle de Service WCF, vous devez utiliser le **ClientCredentials** propriété sur le client WCF pour définir les informations d’identification de mot de passe nom utilisateur pour le système SAP.  
  
-   Si une application qui consomme la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] envoie des messages qui contiennent des informations de base de données sensibles sur une limite de processus à un autre service ou client, assurez-vous que ces messages ont des mesures de sécurité suffisantes appliqués pour fournir les données adéquates protection de votre environnement.  
  
 Pour plus d’informations, consultez [programmation sécurisée avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/secure-programming-with-the-sap-adapter.md).  
  
## <a name="security-best-practices-for-hosting-the-sap-adapter-in-iis"></a>Meilleures pratiques de sécurité pour l’hébergement de l’adaptateur SAP dans IIS  
  
-   Qui héberge le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] dans Microsoft Internet Information Services (IIS) comme un site Web service expose les opérations exposées par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] aux clients Web. Ces opérations peuvent impliquer l’échange de données sensibles sur Internet, donc vous devez prendre des mesures afin de garantir que ces données sont aussi sécurisées que possible.  
  
     [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]fournit deux liaisons standard de transport HTTP : le **BasicHttpBinding** fournit élémentaire de transport HTTP avec aucun mécanisme de sécurité ; le **WSHttpBinding** prend en charge à la fois au niveau du transport et mécanismes de sécurité de niveau message.  
  
     Vous pouvez utiliser la **BasicHttpBinding** via une connexion HTTPS, ou utilisez le **WSHttpBinding** pour aider à protéger vos données. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] inclut le [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)] pour générer le service WCF pour des artefacts LOB. Cet Assistant prend uniquement en charge l’utilisation de **BasicHttpBinding**.  
  
     Vous pouvez également développer une liaison HTTP personnalisée pour tirer parti des mécanismes de sécurité supplémentaire qui fournit de votre environnement. Pour plus d’informations sur la sécurité des fonctionnalités offertes par [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fournit, consultez [sécurisation des Services et les Clients](https://msdn.microsoft.com/library/ms734736.aspx). 
  
## <a name="security-best-practices-for-wcf-diagnostic-tracing-and-message-logging"></a>Meilleures pratiques de sécurité pour le suivi de Diagnostic WCF et la journalisation des messages  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]prend en charge le suivi de diagnostic et de journalisation des messages. Vous configurez le suivi de diagnostic et de journalisation des messages des fichiers de configuration ou à l’aide de Windows Management Instrumentation (WMI). Selon les options de configuration que vous définissez, [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] le suivi de diagnostic ou message de journalisation peut émettre des informations sensibles pour vous connecter de fichiers, où il pourrait potentiellement être exposée à d’observation par les utilisateurs non autorisés.  
  
 Suivez les recommandations fournies dans la documentation WCF pour atténuer les menaces de sécurité potentielles exposées par l’activation de ces fonctionnalités. Au minimum, vous devez observer les meilleures pratiques suivantes pour le suivi de diagnostic et de journalisation des messages :  
  
-   N’activez pas « commentaires » ou le suivi des « informations » dans un environnement de production. Cela peut entraîner une dégradation des performances. Toutefois, vous devez activer « avertissement » et le suivi de « erreur » dans un environnement de production. Si vous activez le traçage, vous devez prendre des mesures de sécurité appropriées pour protéger vos données. Consultez la documentation WCF pour plus d’informations.  
  
-   Assurez-vous que les fichiers de configuration et les fichiers journaux sont protégés par des listes de contrôle d’accès (ACL).  
  
 Les avertissements suivants s’appliquent spécifiquement aux messages échangés entre une application cliente et le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:  
  
-   [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]le suivi de diagnostic peut enregistrer l’en-tête (mais pas le corps) des messages échangés avec le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. L’action du message se trouve dans l’en-tête du message, cela révèle des opérations appelé sur le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] par le client.  
  
-   Si [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] journalisation des messages est activée et `logMessagesAtServiceLevel` est `true`, l’en-tête de message (mais pas le corps du message) des messages échangés entre le client de l’adaptateur et le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] sont enregistrés. L’action du message se trouve dans l’en-tête du message, cela révèle les opérations que le client est appelé sur le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Si `logEntireMessage` est également `true`, le corps du message doivent être enregistré. Cela peut révéler des informations sensibles de la base de données.  
  
     Pour plus d’informations sur l’amélioration de la sécurité lorsque vous activez le traçage de diagnostic, consultez [problèmes de sécurité et des conseils utiles pour le traçage](https://msdn.microsoft.com/library/ms733053.aspx). Pour plus d’informations sur l’amélioration de la sécurité lorsque vous activez la journalisation des messages, consultez [problèmes de sécurité pour la journalisation des messages](https://msdn.microsoft.com/library/ms730318.aspx).  
  
## <a name="see-also"></a>Voir aussi  
[Sécuriser vos applications SAP](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)   
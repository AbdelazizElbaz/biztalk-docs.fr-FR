---
title: "Meilleures pratiques pour sécuriser l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security best practices, for consuming the Siebel adapter with BizTalk Server
- security best practices, for connection between the Siebel adapter and Siebel system
- best practices, security
- security, best practices
- security best practices, for hosting the Siebel adapter in IIS
- security best practices, for WCF diagnostic tracing and message logging
- security best practices, for consuming the Siebel adapter with programming solutions
ms.assetid: da89fcc5-2705-4198-8df6-64b2c532ef41
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f131bb7f0b1d4c4c0106ae5678864517edda0887
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-to-secure-the-siebel-adapter"></a>Meilleures pratiques pour sécuriser l’adaptateur Siebel
Cette section présente les meilleures pratiques à suivre pour protéger plus complètement les données sensibles lorsque vous utilisez ou développerez des applications qui consomment le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].  
  
## <a name="security-best-practices-for-the-connection-between-the-siebel-adapter-and-the-siebel-system"></a>Meilleures pratiques de sécurité pour la connexion entre l’adaptateur Siebel et le système Siebel  
  
-   Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] prend en charge le chiffrement mscrypto ou rsa sur les données échangées entre l’adaptateur et le système Siebel. Pour garantir la confidentialité des données qui sont échangées entre l’adaptateur et le système Siebel, vous devez activer un de ces modes de chiffrement.  
  
-   Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne fournit pas de mécanismes pour garantir l’intégrité des données ou pour fournir pour l’authentification et d’autorisation sur les données qui sont échangées entre lui-même et le système Siebel. Vous devez fournir ces mécanismes, si ces problèmes existent dans votre environnement.  
  
-   Ne fournissez pas les informations d’identification de mot de passe utilisateur pour le système Siebel dans l’URI de connexion. Consultez le reste de cette rubrique pour d’autres méthodes permettent de fournir des informations d’identification pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
 Pour plus d’informations, consultez [sécurité entre Siebel et de la carte](../../adapters-and-accelerators/adapter-siebel/security-between-the-siebel-system-and-the-adapter.md)
  
## <a name="security-best-practices-for-consuming-the-siebel-adapter-with-biztalk-server"></a>Meilleures pratiques de sécurité pour l’utilisation de l’adaptateur Siebel à BizTalk Server  
  
-   Ne fournissez pas les informations d’identification de mot de passe utilisateur pour le système Siebel dans l’URI de connexion.  
  
-   Lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], entrez les informations d’identification de mot de passe de nom utilisateur pour le système Siebel à partir de la **sécurité** onglet de la **configurer l’adaptateur** boîte de dialogue.  
  
-   Lorsque vous configurez l’adaptateur BizTalk WCF-Custom pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] sur un port d’envoi, entrez les informations d’identification de mot de passe de nom utilisateur pour le système Siebel à partir de la **informations d’identification** onglet du **configurer le Transport personnalisé WCF**  boîte de dialogue.  
  
-   Lorsque vous configurez l’adaptateur BizTalk WCF-Custom pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] sur un emplacement de réception, entrez les informations d’identification de mot de passe de nom utilisateur pour le système Siebel à partir de la **autres** onglet du **configurer le Transport personnalisé WCF**  boîte de dialogue.  
  
 Pour plus d’informations, consultez [sécurité avec l’adaptateur Siebel et BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md)
  
## <a name="security-best-practices-for-consuming-the-siebel-adapter-with-programming-solutions"></a>Meilleures pratiques de sécurité pour l’utilisation de l’adaptateur Siebel avec les Solutions de programmation  
  
-   Il est parfois nécessaire fournir des informations d’identification de mot de passe de l’utilisateur pour le système Siebel dans l’URI ; de connexion Toutefois, si possible, vous devez éviter cette opération.  
  
-   Lorsque vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], entrez les informations d’identification de mot de passe de nom utilisateur pour le système Siebel à partir de la **sécurité** onglet de la **configurer l’adaptateur** boîte de dialogue.  
  
-   Dans la programmation du modèle de canal WCF, vous devez utiliser le **informations d’identification** propriété sur la fabrication de canal pour définir des informations d’identification de mot de passe pour le système Siebel de l’utilisateur.  
  
-   Dans la programmation du modèle de Service WCF, vous devez utiliser le **ClientCredentials** propriété sur le client WCF pour définir des informations d’identification de mot de passe pour le système Siebel de l’utilisateur.  
  
-   Si une application qui consomme la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] envoie des messages qui contiennent des informations de base de données sensibles sur une limite de processus à un autre service ou client, assurez-vous que ces messages ont des mesures de sécurité suffisantes appliqués pour fournir les données adéquates protection de votre environnement.  
  
 Pour plus d’informations, consultez [programmation sécurisée avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/secure-programming-with-the-siebel-adapter.md) 
  
## <a name="security-best-practices-for-hosting-the-siebel-adapter-in-iis"></a>Meilleures pratiques de sécurité pour l’hébergement de l’adaptateur Siebel dans IIS  
  
-   Qui héberge le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] dans Microsoft Internet Information Services (IIS) comme un site Web service expose les opérations exposées par le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] aux clients Web. Ces opérations peuvent impliquer l’échange de données sensibles sur Internet, donc vous devez prendre des mesures afin de garantir que ces données sont aussi sécurisées que possible.  
  
     [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]fournit deux liaisons standard de transport HTTP : le **BasicHttpBinding** fournit élémentaire de transport HTTP avec aucun mécanisme de sécurité ; le **WSHttpBinding** prend en charge à la fois au niveau du transport et mécanismes de sécurité de niveau message.  
  
     Vous pouvez utiliser la **BasicHttpBinding** via une connexion HTTPS, ou utilisez le **WSHttpBinding** pour aider à protéger vos données. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] inclut le [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)] pour générer des services WCF pour des artefacts LOB. Cet Assistant prend uniquement en charge l’utilisation de **BasicHttpBinding**.  
  
     Vous pouvez également développer une liaison HTTP personnalisée pour tirer parti des mécanismes de sécurité supplémentaire qui fournit de votre environnement. Pour plus d’informations sur la sécurité des fonctionnalités offertes par [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fournit, consultez [sécurisation des Services et les Clients](https://msdn.microsoft.com/library/ms734736.aspx).
  
## <a name="security-best-practices-for-wcf-diagnostic-tracing-and-message-logging"></a>Meilleures pratiques de sécurité pour le suivi de Diagnostic WCF et la journalisation des messages  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]prend en charge le suivi de diagnostic et de journalisation des messages. Vous configurez le suivi de diagnostic et de journalisation des messages des fichiers de configuration ou à l’aide de Windows Management Instrumentation (WMI). Selon les options de configuration que vous définissez, [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] le suivi de diagnostic ou message de journalisation peut émettre des informations sensibles pour vous connecter de fichiers, où il pourrait potentiellement être exposée à d’observation par les utilisateurs non autorisés.  
  
 Suivez les recommandations fournies dans la documentation WCF pour atténuer les menaces de sécurité potentielles exposées par l’activation de ces fonctionnalités. Au minimum, vous devez observer les meilleures pratiques suivantes pour le suivi de diagnostic et de journalisation des messages :  
  
-   N’activez pas « commentaires » ou le suivi des « informations » dans un environnement de production. Cela peut entraîner une dégradation des performances. Toutefois, vous devez activer « avertissement » et le suivi de « erreur » dans un environnement de production. Si vous activez le traçage, vous devez prendre des mesures de sécurité appropriées pour protéger vos données. Consultez la documentation WCF pour plus d’informations.  
  
-   Assurez-vous que les fichiers de configuration et les fichiers journaux sont protégés par des listes de contrôle d’accès (ACL).  
  
 Les avertissements suivants s’appliquent spécifiquement aux messages échangés entre une application cliente et le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]:  
  
-   [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]le suivi de diagnostic peut enregistrer l’en-tête (mais pas le corps) des messages échangés avec le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. L’action du message se trouve dans l’en-tête du message, cela révèle des opérations appelé sur le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] par le client.  
  
-   Si [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] journalisation des messages est activée et `logMessagesAtServiceLevel` est `true`, l’en-tête de message (mais pas le corps du message) des messages échangés entre le client de l’adaptateur et le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] sont enregistrés. L’action du message se trouve dans l’en-tête du message, cela révèle les opérations que le client est appelé sur le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Si `logEntireMessage` est également `true`, le corps du message doivent être enregistré. Cela peut révéler des informations sensibles de la base de données.  
  
 Pour plus d’informations sur l’amélioration de la sécurité lorsque vous activez le traçage de diagnostic, consultez [problèmes de sécurité et des conseils utiles pour le traçage](https://msdn.microsoft.com/library/ms733053.aspx). Pour plus d’informations sur l’amélioration de la sécurité lorsque vous activez la journalisation des messages, consultez [problèmes de sécurité pour la journalisation des messages](https://msdn.microsoft.com/library/ms730318.aspx).
  
## <a name="see-also"></a>Voir aussi  
[Sécuriser vos applications Siebel](../../adapters-and-accelerators/adapter-siebel/secure-your-siebel-applications.md)
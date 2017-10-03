---
title: "Meilleures pratiques pour sécuriser l’adaptateur Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d492d22-2a1f-4b91-9000-a4d74c6fb2fb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd530d653f1fb5403d1632d94ed688ad7ca8a3b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-to-secure-the-oracle-e-business-suite-adapter"></a>Meilleures pratiques pour sécuriser l’adaptateur Oracle E-Business Suite
Cette section présente les meilleures pratiques à suivre pour protéger plus complètement les données sensibles lorsque vous utilisez ou développerez des applications qui consomment le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)].  
  
## <a name="security-best-practices-for-the-connection-between-the-oracle-e-business-adapter-and-the-oracle-database"></a>Meilleures pratiques de sécurité pour la connexion entre l’adaptateur Oracle E-Business et de la base de données Oracle  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne fournit aucune prise en charge pour aider à sécuriser la communication entre elle et Oracle E-Business Suite. Vous devez fournir un mécanisme pour garantir un niveau adéquat de sécurité pour les données échangées entre l’adaptateur et la base de données Oracle.  
  
-   Ne fournissez pas les informations d’identification de mot de passe utilisateur pour la base de données Oracle dans l’URI de connexion. Consultez les sections suivantes pour les autres méthodes permettent de fournir des informations d’identification pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] vous permet également d’utiliser l’authentification Windows lors de la connexion à Oracle E-Business Suite pour générer des métadonnées et effectuer des opérations, que ce soit via [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ou [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Avant d’utiliser l’authentification Windows, vous devez effectuer les étapes répertoriées dans [se connecter à Oracle E-Business Suite à l’aide de l’authentification Windows](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md).  
  
 Pour plus d’informations, consultez [sécurité entre Oracle E-Business Suite et de la carte](../../adapters-and-accelerators/adapter-oracle-ebs/security-between-oracle-e-business-suite-and-the-adapter.md).  
  
## <a name="security-best-practices-for-consuming-the-oracle-e-business-adapter-with-biztalk-server"></a>Meilleures pratiques de sécurité pour l’utilisation de l’adaptateur Oracle E-Business avec BizTalk Server  
  
-   Vous devez éviter de fournir des informations d’identification de mot de passe utilisateur pour Oracle E-Business Suite dans l’URI de connexion.  
  
-   Lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], entrez les informations d’identification de mot de passe nom utilisateur pour Oracle E-Business Suite à partir de la **sécurité** onglet de la **configurer l’adaptateur** boîte de dialogue.  
  
-   Lorsque vous configurez l’adaptateur BizTalk WCF-Custom pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] sur un port d’envoi, entrez les informations d’identification de mot de passe de nom utilisateur pour la base de données Oracle à partir de la **informations d’identification** onglet du **configurer le Transport personnalisé WCF**  boîte de dialogue.  
  
-   Lorsque vous configurez l’adaptateur BizTalk WCF-Custom pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] sur un emplacement de réception, entrez les informations d’identification de mot de passe de nom utilisateur pour la base de données Oracle à partir de la **autres** onglet du **configurer le Transport personnalisé WCF**  boîte de dialogue.  
  
-   Après avoir exporté un fichier de liaison à partir d’une application dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez supprimer manuellement la valeur de la **OraclePassword** (disponible en texte clair) de la propriété de liaison à partir du fichier de liaison et de spécifier à nouveau sur chaque ordinateur hôte où la liaison exportée sera utilisé.  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] vous permet également d’utiliser l’authentification Windows lors de la connexion à Oracle E-Business Suite pour générer des métadonnées et effectuer des opérations, que ce soit via [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ou [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Avant d’utiliser l’authentification Windows, vous devez effectuer les étapes répertoriées dans [se connecter à Oracle E-Business Suite à l’aide de l’authentification Windows](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md).  
  
-   Si une application qui consomme la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] envoie des messages qui contiennent des informations de base de données sensibles sur une limite de processus à un autre service ou client, assurez-vous que ces messages ont des mesures de sécurité suffisantes appliqués pour fournir les données adéquates protection de votre environnement.  
  
 Pour plus d’informations, consultez [sécurité avec l’adaptateur Oracle E-Business Suite et BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/security-with-the-oracle-e-business-suite-adapter-and-biztalk-server.md).  
  
## <a name="security-best-practices-for-consuming-the-oracle-e-business-adapter-with-programming-solutions"></a>Meilleures pratiques de sécurité pour l’utilisation de l’adaptateur de E-Business Oracle avec des Solutions de programmation  
  
-   Vous devez éviter de fournir des informations d’identification de mot de passe utilisateur pour la base de données Oracle dans l’URI de connexion.  
  
-   Lorsque vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], entrez les informations d’identification de mot de passe de nom utilisateur pour la base de données Oracle à partir de la **sécurité** onglet de la **configurer l’adaptateur** boîte de dialogue.  
  
-   Dans la programmation de modèle de canal WCF, vous devez utiliser le **informations d’identification** propriété sur la fabrication de canal pour définir les informations d’identification de mot de passe nom utilisateur pour la base de données Oracle.  
  
-   Dans la programmation de modèle de service WCF, vous devez utiliser le **ClientCredentials** propriété sur le client WCF pour définir les informations d’identification de mot de passe nom utilisateur pour la base de données Oracle.  
  
-   Si une application qui consomme la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] envoie des messages qui contiennent des informations de base de données sensibles sur une limite de processus à un autre service ou client, assurez-vous que ces messages ont des mesures de sécurité suffisantes appliqués pour fournir les données adéquates protection de votre environnement.  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] vous permet également d’utiliser l’authentification Windows lors de la connexion à Oracle E-Business Suite pour générer des métadonnées et effectuer des opérations, que ce soit via [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ou [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Avant d’utiliser l’authentification Windows, vous devez effectuer les étapes répertoriées dans [se connecter à Oracle E-Business Suite à l’aide de l’authentification Windows](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md).  
  
 Pour plus d’informations, consultez [considérations de sécurité pour les adaptateurs](../../core/security-considerations-for-adapters.md).  
  
## <a name="security-best-practices-for-hosting-the-oracle-e-business-adapter-in-iis"></a>Meilleures pratiques de sécurité pour l’hébergement de l’adaptateur Oracle E-Business dans IIS  
 Qui héberge le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] dans Microsoft Internet Information Services (IIS) comme un site Web service expose les opérations exposées par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] aux clients Web. Ces opérations peuvent impliquer l’échange de données sensibles sur Internet, donc vous devez prendre des mesures afin de garantir que ces données sont aussi sécurisées que possible.  
  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]fournit deux liaisons standard de transport HTTP : le **BasicHttpBinding** fournit élémentaire de transport HTTP avec aucun mécanisme de sécurité ; le **WSHttpBinding** prend en charge à la fois au niveau du transport et mécanismes de sécurité de niveau message.  
  
 Vous pouvez utiliser la **BasicHttpBinding** via une connexion HTTPS, ou utilisez le **WSHttpBinding** pour aider à protéger vos données. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] inclut le [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)] pour générer le service WCF pour des artefacts LOB. Cet Assistant prend uniquement en charge l’utilisation de **BasicHttpBinding**.  
  
 Vous pouvez également développer une liaison HTTP personnalisée pour tirer parti des mécanismes de sécurité supplémentaire qui fournit de votre environnement. Pour plus d’informations sur la sécurité des fonctionnalités offertes par [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fournit, consultez « Sécurisation des Services et des Clients » à l’adresse [http://go.microsoft.com/fwlink/?LinkId=89725](http://go.microsoft.com/fwlink/?LinkId=89725).  
  
## <a name="security-best-practices-for-wcf-diagnostic-tracing-and-message-logging"></a>Meilleures pratiques de sécurité pour le suivi de Diagnostic WCF et la journalisation des messages  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]prend en charge le suivi de diagnostic et de journalisation des messages. Vous configurez le suivi de diagnostic et de journalisation des messages des fichiers de configuration ou à l’aide de Windows Management Instrumentation (WMI). Selon les options de configuration que vous définissez, [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] le suivi de diagnostic ou message de journalisation peut émettre des informations sensibles pour vous connecter de fichiers, où il pourrait potentiellement être exposée à d’observation par les utilisateurs non autorisés.  
  
 Suivez les recommandations fournies dans la documentation WCF pour atténuer les menaces de sécurité potentielles exposées par l’activation de ces fonctionnalités. Au minimum, vous devez observer les meilleures pratiques suivantes pour le suivi de diagnostic et de journalisation des messages :  
  
-   N’activez pas « commentaires » ou le suivi des « informations » dans un environnement de production. Cela peut entraîner une dégradation des performances. Toutefois, vous devez activer « avertissement » et le suivi de « erreur » dans un environnement de production. Si vous activez le traçage, vous devez prendre des mesures de sécurité appropriées pour protéger vos données. Consultez la documentation WCF pour plus d’informations.  
  
-   Assurez-vous que les fichiers de configuration et les fichiers journaux sont protégés par des listes de contrôle d’accès (ACL).  
  
 Les avertissements suivants s’appliquent spécifiquement aux messages échangés entre une application cliente et le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]:  
  
-   [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]le suivi de diagnostic peut enregistrer l’en-tête (mais pas le corps) des messages échangés avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. L’action du message se trouve dans l’en-tête du message, cela révèle des opérations appelé sur le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] par le client.  
  
-   Si [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] journalisation des messages est activée et `logMessagesAtServiceLevel` est `true`, l’en-tête de message (mais pas le corps du message) des messages échangés entre le client de l’adaptateur et le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] sont enregistrés. L’action du message se trouve dans l’en-tête du message, cela révèle les opérations que le client est appelé sur le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Si `logEntireMessage` est également `true`, le corps du message doivent être enregistré. Cela peut révéler des informations sensibles de la base de données.  
  
 Pour plus d’informations sur l’amélioration de la sécurité lorsque vous activez le traçage de diagnostic, consultez « Sécurité préoccupations utiles conseils pour le suivi et » à [http://go.microsoft.com/fwlink/?LinkId=89796](http://go.microsoft.com/fwlink/?LinkId=89796). Pour plus d’informations sur l’amélioration de la sécurité lorsque vous activez la journalisation des messages, consultez « Sécurité préoccupations de journalisation des messages » à [http://go.microsoft.com/fwlink/?LinkId=89797](http://go.microsoft.com/fwlink/?LinkId=89797).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser vos applications Oracle eBusiness Suite](secure-your-oracle-ebs-applications.md)
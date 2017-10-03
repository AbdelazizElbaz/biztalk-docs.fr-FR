---
title: "Meilleures pratiques pour le déploiement d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53852303-d368-4f9e-b4e2-f5918f65000b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25d24eda11d9547b545445239e783ac3bfee4057
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-deploying-an-application"></a>Meilleures pratiques pour le déploiement d’une Application
Cette rubrique répertorie les meilleures pratiques à suivre pour déployer des applications BizTalk.  
  
## <a name="deploying-a-biztalk-application"></a>Déploiement d’une Application BizTalk  
 **Procédures de déploiement d’application document**  
  
-   Assurez-vous que toutes les procédures utilisées dans le déploiement d’application sont documentés en détail, afin que vous ayez un enregistrement de la façon dont le déploiement a été effectué et saurez comment déployer davantage ou annuler le déploiement. Tout ce qui n’est pas un script doit être documenté avec des instructions détaillées. Cela doit inclure la documenter les modifications apportées aux systèmes externes et de déploiement des composants tiers.  
  
 **Déploiement d’applications de script**  
  
-   Générer un script des étapes de déploiement application autant que possible. Écriture de scripts permet de réduire le risque d’erreur humaine pendant le processus de déploiement.  
  
## <a name="creating-a-biztalk-application"></a>Création d’une Application BizTalk  
 **Script de la création de fichiers d’application et le fichier .msi BizTalk**  
  
-   BtsTask.exe peut servir à la création d’applications BizTalk de script. Si la création des applications est l’objet d’un script, puis les packages peuvent être créées automatiquement à l’aide d’un processus automatisé sur un serveur de builds. Pour plus d’informations sur la création d’applications de script, consultez [déploiement et la gestion des Applications BizTalk](http://go.microsoft.com/fwlink/?LinkID=154210) (http://go.Microsoft.com/fwlink/?) LinkID = 154210) et le [BizTalk Server 2006 : présentation du déploiement d’Application BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=101599) (http://go.Microsoft.com/fwlink/?) LinkID = 101599) livre blanc.  
  
    > [!NOTE]  
    >  Le livre blanc s’applique également aux [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
## <a name="deploying-a-biztalk-assembly"></a>Déploiement d’un Assembly BizTalk  
 **Jamais déployer un assembly à partir de Visual Studio sur un ordinateur de production**  
  
-   Pendant le processus de développement, un développeur redéploient souvent les assemblys à partir de Visual Studio. Pour activer le redéploiement, Visual Studio peut annuler le déploiement, supprimer la liaison, arrêter et désinscrire les artefacts inclus dans les assemblys. Bien que tout ceci soit nécessaire et approprié à l'environnement de développement, cela peut entraîner des conséquences inattendues et indésirables dans l'environnement de production. Pour cette raison, ainsi que pour empêcher toute personne de déploiement d’un assembly à partir de Visual Studio sur un ordinateur de production, nous vous recommandons de ne jamais installer de Visual Studio sur un ordinateur de production.  
  
-   En outre, ne faites jamais référence à une base de données de production à partir d'un ordinateur exécutant Visual Studio.  
  
## <a name="adding-artifacts-to-a-biztalk-application"></a>Ajout d’artefacts à une Application BizTalk  
 **Groupe d’artefacts associés dans une seule application**  
  
-   Placez autant que possible les artefacts associés dans la même application BizTalk. Vous pouvez gérer et déployer les artefacts dans une seule entité, et ainsi simplifier la gestion. Vous avez la possibilité de grouper les artefacts qui prennent en charge le même processus d'entreprise ou ceux qui réalisent les mêmes fonctions au sein d'une application.  
  
 **Déploiement d’artefacts partagés dans une application distincte**  
  
-   Si les artefacts doivent être partagés par plusieurs applications, déployez-les dans une application distincte. Si, par exemple, deux applications partagent le même schéma, placez ce dernier dans une application distincte. Nous le recommandons, car seul l’artefact dans un groupe BizTalk peut avoir un identificateur unique local (LUID). Un LUID se compose du nom d’artefact et éventuellement d’autres attributs. Si vous incluez un artefact dans une application, puis créez une référence à celui-ci à partir d’une autre application, l’application de référence peut ne pas fonctionne correctement lorsque vous arrêtez l’application contenant l’artefact.  
  
     La méthode conseillée s'applique à tous les types d'artefact sauf pour les fichiers, comme les fichiers Readme (Lisezmoi) et les scripts, qui sont ajoutés à l'application en tant que type Fichier d'artefact, Il s’agit, car plusieurs artefacts de fichier portant le même nom peut être déployé dans un groupe BizTalk. Vous pouvez par conséquent utiliser un fichier ayant le même nom dans plusieurs applications. Dans ce cas, l’arrêt d’une application n’affectera pas l’autre application. Pour plus d’informations sur l’ajout d’artefacts d’un fichier, consultez [l’ajout d’un fichier à une Application](http://go.microsoft.com/fwlink/?LinkId=154997) (http://go.microsoft.com/fwlink/?LinkId=154997).  
  
 **Déployer un site Web partagé dans une application distincte**  
  
-   Si plusieurs solutions d'entreprise doivent se partager un même site Web, déployez ce dernier dans une application distincte. En effet, lorsque vous désinstallez une application BizTalk, le répertoire virtuel du site Web qui fait partie de l'application est supprimé, même si le site est en cours d'exécution. Et si le site Web est partagé avec une autre solution d'entreprise, cette dernière ne fonctionnera plus correctement.  
  
 **Déploiement de stratégies partagées dans une application distincte**  
  
-   Si plusieurs applications utilisent la même stratégie, vous devez la déployer dans une application distincte plutôt que de créer une référence d'une application à l'autre, car lorsque vous arrêtez une application, ses stratégies ne sont plus déployées. Si vous arrêtez une application contenant une stratégie utilisée par une autre application, la stratégie ne fonctionnera plus dans l'application.  
  
 **Déploiement de certificats partagés dans une application distincte**  
  
-   Si vous utilisez un certificat sur un port d'envoi ou un emplacement de réception dans plusieurs applications, vous devez déployer le certificat dans une application distincte, puis référencer cette application depuis les autres applications qui utilisent le certificat, Il s’agit, car seul artefact dans un groupe BizTalk peut avoir un LUID unique, vous ne pourrez pas importer le même certificat dans différentes applications. Si vous tentez d'importer deux applications utilisant le même certificat, la première importation réussira, la seconde non. Dans ce cas, l'utilisation de l'option d'importation Remplacer ne résout pas le problème, étant donné que le certificat que vous souhaitez remplacer existe dans une autre application.  
  
## <a name="exporting-and-importing-a-biztalk-application"></a>Exportation et importation d’une Application BizTalk  
 **Lors du déploiement des fichiers .msi volumineux, vous devrez peut-être augmenter le délai d’expiration de transaction par défaut des composants COM + utilisés par BizTalk Server pour déployer des applications**  
  
-   Si vous tentez de déployer un fichier .msi est très élevée (plus de 100 Mo), puis l’application ne peut pas être déployée dans le délai d’expiration de transaction par défaut des composants COM + utilisés par BizTalk Server pendant le déploiement de l’application. Si les transactions associées à ces COM + composants délai d’attente avant le déploiement terminé, le déploiement échoue. Si vous déployez des fichiers .msi très volumineux, envisagez de prendre une de ces approches pour atténuer ce problème :  
  
-   Déployez plusieurs fichiers .msi plus petits au lieu d’un fichier .msi de grande taille.  
  
    -   Augmenter le délai d’expiration de transaction par défaut de 3 000 secondes associé à la Microsoft.BizTalk.ApplicationDeployment.Group et les composants Microsoft.BizTalk.Deployment.DeployerComponent dans l’interface de gestion des Services de composants. Ces composants appartiennent respectivement aux applications Microsoft.BizTalk.ApplicationDeployment.Engine et Microsoft.Biztalk.Deployment COM +. Pour plus d’informations, consultez l’article de la Base de connaissances Microsoft 287499, [comment modifier la valeur de délai d’attente de Transaction pour MTS ou COM +](http://go.microsoft.com/fwlink/?LinkId=109589) (http://go.microsoft.com/fwlink/?LinkId=109589).  
  
 **Empêcher les liaisons d’être remplacé**  
  
-   Pour éviter que les liaisons de l'application exportée ne remplacent les liaisons de l'application dans laquelle vous importez le fichier .msi, ne sélectionnez pas le fichier de liaison en tant que ressource à exporter pendant l'opération d'exportation.  
  
 **Assurez-vous que le fichier .msi est sécurisé**  
  
-   Un fichier .msi peut contenir des données sensibles. Veillez à prendre des mesures pour garantir que le fichier est sécurisé. Pour plus d’informations sur la sécurité du fichier .msi, consultez [sécurité et Windows Installer](http://go.microsoft.com/fwlink/?LinkId=154998) (http://go.microsoft.com/fwlink/?LinkId=154998).  
  
 **Assurez-vous que le fichier de liaison est sécurisé**  
  
-   Un fichier de liaison peut contenir des données sensibles. Veillez à prendre des mesures pour garantir que le fichier est sécurisé.  
  
 **Planification exporte lorsqu’aucun apporte des modifications à un artefact**  
  
-   Planifier les opérations d’exportation pendant les heures lorsque les utilisateurs ne sont pas susceptibles d’apporter des modifications à des artefacts. Cela peut être important car si un utilisateur modifie un artefact basé sur la base de données, un répertoire virtuel, un certificat ou une stratégie pendant une opération d’exportation est en cours d’exécution, les modifications seront répercutées dans le fichier .msi exporté.  
  
## <a name="importing-a-biztalk-application"></a>L’importation d’une Application BizTalk  
 **Script de l’importation des fichiers .msi**  
  
-   BtsTask.exe peut servir à l’importation des fichiers du fichier .msi BizTalk existants de script. Pour plus d’informations sur les scripts de l’importation de fichier .msi, consultez [déploiement et la gestion des Applications BizTalk](http://go.microsoft.com/fwlink/?LinkID=154210) (http://go.Microsoft.com/fwlink/?) LinkID = 154210) et le [BizTalk Server 2006 : présentation du déploiement d’Application BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=101599) (http://go.Microsoft.com/fwlink/?) LinkID = 101599) livre blanc.  
  
    > [!NOTE]  
    >  Le livre blanc s’applique également aux [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
-   Vous pouvez ajouter des scripts à exécuter en tant que scripts de pré-traitement ou de post-traitement. Toutefois, vous devez inclure une logique dans vos scripts pour vérifier les variables d’environnement pour déterminer le contexte dans lequel le script s’exécute dans (une importation, l’installation ou la désinstallation) et traiter en conséquence. Pour plus d’informations sur l’utilisation de scripts de pré-traitement et post-traitement, voir [à l’aide de Scripts de pré-traitement et post-traitement au déploiement d’Application personnaliser](http://go.microsoft.com/fwlink/?LinkId=154995) (http://go.microsoft.com/fwlink/?LinkId=154995).  
  
 **Vérifier l’existence d’artefacts**  
  
-   Lorsqu’une application que vous importez comporte une référence à une autre application, BizTalk Server vérifie que l’application référencée existe. Toutefois, il ne vérifie pas que les artefacts sur lequel votre application possède des dépendances sont inclus dans l’application référencée. Lorsque vous importez une application qui a des dépendances pour les artefacts dans une autre application, nous vous conseillons de vérifier que l’application référencée contienne l’ou les artefacts requis.  
  
 **L’importation d’un fichier .msi vous empêche de le stockage des assemblys modifiés dans le global assembly cache**  
  
-   Pour mettre à jour les artefacts dans une application, importer les artefacts modifiés ou mis à jour à partir d’un fichier .msi dans l’application. Si vous n’utilisez pas un fichier .msi pour importer les artefacts, vous devez mettre à jour tous les serveurs dans le groupe en stockant les assemblys modifiés dans le global assembly cache.  
  
 **Traitement de l’hôte les groupes à mettre à jour un sous-ensemble du nombre total de serveurs**  
  
-   Lors de la mise à jour des artefacts dans une application, vous devez normalement mettre à jour tous les serveurs dans un groupe BizTalk. Cependant, si vous utilisez des groupes de traitement de l’hôte, il vous suffit de mettre à jour un sous-ensemble des serveurs dans le groupe de total.  
  
 **Si une opération d’importation expire, fractionnez l’application en fichiers .msi supplémentaires**  
  
-   Une opération d’importation expire si elle dépasse 3 600 secondes. Si vous essayez d’importer un fichier .msi et que l’opération arrive à expiration, vous devez diviser le contenu de l’application en plusieurs fichiers .msi en réexportant l’application et en sélectionnant un sous-ensemble d’artefacts à exporter. Pour plus d’informations sur l’exportation d’une application dans un fichier .msi, consultez [comment exporter une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154848) (http://go.microsoft.com/fwlink/?LinkID=154848).
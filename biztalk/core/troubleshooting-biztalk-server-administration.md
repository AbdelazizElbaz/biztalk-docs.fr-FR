---
title: "Résolution des problèmes d’Administration de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9dfb56b0-352f-4012-b030-087bbcfe09d4
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d89f81bbaf15dfb0c87de91659888d70a2345a6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-biztalk-server-administration"></a>Résolution des problèmes d’Administration de BizTalk Server
Cette section centralise les informations sur les problèmes connus rencontrés lors de l'utilisation de la console Administration de BizTalk Server.  
  
 Outre les problèmes connus suivants, [problèmes courants et solutions avec la Console Administration de BizTalk](http://social.technet.microsoft.com/wiki/contents/articles/common-issues-and-resolutions-with-the-biztalk-server-administration-console.aspx) fournit des informations supplémentaires.  
  
## <a name="known-issues"></a>Problèmes connus  
  
#### <a name="delay-in-entsso-service-prevents-biztalk-server-service-from-starting"></a>L'attente liée au démarrage du service d'authentification unique de l'entreprise empêche le démarrage du service BizTalk Server  
  
##### <a name="problem"></a>Problème  
 Le redémarrage de votre ordinateur sans que le démarrage automatique du coordinateur DTC soit défini peut empêcher le démarrage du service BizTalk Server.  
  
##### <a name="cause"></a>Cause  
 Un délai nécessaire au démarrage du service d'authentification unique de l'entreprise supérieur à celui autorisé par la durée d'expiration du service BizTalk Server peut provoquer ce problème.  
  
##### <a name="solution"></a>Solution  
 Pour résoudre ce problème, définissez le démarrage automatique du coordinateur DTC.  
  
#### <a name="sql-resources-may-become-locked"></a>Des ressources SQL peuvent être verrouillées  
  
##### <a name="problem"></a>Problème  
 L'erreur suivante peut se produire :  
  
 **La transaction (ID de processus 95) a été bloquée sur les ressources de verrouillage par un autre processus et a été choisie comme victime. Réexécutez la transaction.**  
  
##### <a name="cause"></a>Cause  
 Dans cette situation très rare, les opérations d'administration effectuées par un utilisateur entraînent l'exclusion d'un autre utilisateur de l'administration des bases de données.  
  
##### <a name="solution"></a>Solution  
 Le problème doit se résoudre rapidement de lui-même. Réessayez l'opération après quelques instants.  
  
#### <a name="sql-database-may-become-locked"></a>La base de données SQL peut être verrouillée  
  
##### <a name="problem"></a>Problème  
 Les utilisateurs peuvent être exclus de la base de données SQL. Divers messages d'erreur peuvent être renvoyés.  
  
##### <a name="cause"></a>Cause  
 Dans certains cas, les opérations d'écriture dans la base de données effectuées par un utilisateur provoquent l'exclusion d'un autre utilisateur de la base de données.  
  
##### <a name="solution"></a>Solution  
 Le problème doit se résoudre rapidement de lui-même. Réessayez l'opération après quelques instants.  
  
#### <a name="termination-of-multiple-service-instances-in-a-multiple-messagebox-environment-fails-with-an-error"></a>L'arrêt de plusieurs instances de service dans un environnement incluant plusieurs bases de données MessageBox échoue avec une erreur  
  
##### <a name="problem"></a>Problème  
 Les tentatives d'arrêt de plusieurs instances de service à l'aide de la console Administration de BizTalk Server échouent et une erreur similaire à celle indiquée ci-après est affichée :  
  
 Le serveur SQL Server a bloqué l'accès à la procédure « sys.xp_sqlagent_enum_jobs » du composant « Agent XPs » car celui-ci est désactivé dans le cadre de la configuration de sécurité du serveur.  
  
> [!NOTE]
>  Ce problème se produit dans un environnement incluant plusieurs bases de données MessageBox.  
  
##### <a name="cause"></a>Cause  
 Ce problème peut se produire dans un environnement messagebox si le travail de l’agent SQL ' Operations_OperateOnInstances_OnMaster_\<*dbName*>' n'est pas exécuté sur les bases de données messagebox secondaire. Ce travail doit être exécuté pour propager les informations des bases de données MessageBox secondaires à la base de données MessageBox principale. L'exécution de ce travail échoue si celui-ci n'est pas activé ou si un échec de connexion se produit.  
  
##### <a name="solution"></a>Solution  
 Si vous utilisez la console Administration de BizTalk pour effectuer des opérations sur plusieurs instances de service simultanément et que votre environnement BizTalk Server est configuré avec plusieurs bases de données messagebox, vérifiez que le travail de l’Agent SQL Server nommé « Operations_ OperateOnInstances_OnMaster_\<*dbName*>' est activée sur toutes les bases de données messagebox (non-master) secondaire. En outre, le service SQL Server Agent sur l'ordinateur SQL Server qui héberge les bases de données MessageBox secondaires doit être exécuté comme compte inclus dans le rôle BTS_SQLAGENT_USER de la base de données MessageBox secondaire.  
  
> [!NOTE]
>  \<*dbname*> est un espace réservé pour le nom réel de la base de données messagebox de BizTalk.  
  
 Pour ajouter le compte de service SQL Server Agent au rôle BTS_SQLAGENT_USER de la base de données MessageBox secondaire, procédez comme suit :  
  
 **Sur le serveur SQL Server 2008**  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008**, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Lorsque vous y êtes invité choisir le **type de serveur** de **moteur de base de données** et entrez ou sélectionnez le **nom du serveur** qui héberge la base de données messagebox secondaire.  
  
3.  Cliquez pour développer **bases de données**, développez la base de données messagebox secondaire, cliquez pour développer **sécurité**, cliquez pour développer **rôles**, cliquez pour développer  **Rôles de base de données**, puis double-cliquez sur le rôle de base de données BTS_SQLAGENT_USER.  
  
4.  Cliquez sur le bouton **Ajouter** .  
  
5.  Cliquez sur **Parcourir**, sélectionnez un groupe dont le compte de service de l’Agent SQL Server est un membre de, puis cliquez sur **OK**.  
  
> [!NOTE]
>  Si le compte de service SQL Server Agent n'est pas membre du groupe spécifié, vous devez l'ajouter au groupe.  
  
#### <a name="changes-applied-in-one-instance-of-the-biztalk-administration-console-are-not-automatically-updated-in-other-instances-of-the-biztalk-administration-console"></a>Les modifications apportées dans une instance de la console Administration de BizTalk ne sont pas automatiquement répercutées dans les autres instances de la console  
  
##### <a name="problem"></a>Problème  
 Si plusieurs instances de la console Administration de BizTalk sont simultanément connectées au même groupe BizTalk Server, les modifications apportées dans une instance ne sont pas automatiquement répercutées dans les autres. Cela peut générer des erreurs de violation d'accès lors de la tentative de modification d'un artefact affiché dans une instance de la console si l'état de celui-ci ne correspond pas à l'état réel de l'artefact stocké dans la base de données de gestion BizTalk.  
  
##### <a name="cause"></a>Cause  
 Chaque instance de la console Administration de BizTalk gère son propre cache de la configuration de groupe BizTalk et répercute uniquement les modifications dans celui-ci. Le cache est uniquement mis à jour lors de l'actualisation de la console.  
  
##### <a name="resolution"></a>Résolution  
 Si vous recevez des erreurs de violation d’accès concurrentiel dans la console Administration de BizTalk, mettre à jour le cache pour l’instance de la console Administration de BizTalk en cliquant sur le **Actualiser** bouton sur la console Administration de BizTalk barre d’outils ou en appuyant sur la **F5** clé.  
  
#### <a name="failed-to-execute-action-stop-error-occurs-when-you-attempt-to-stop-an-orchestration-with-the-biztalk-administration-console"></a>L'erreur « Impossible d'exécuter l'action Arrêter » se produit lorsque vous tentez d'arrêter une orchestration à l'aide de la console Administration de BizTalk  
  
##### <a name="problem"></a>Problème  
 Lorsque vous tentez d'arrêter une orchestration à l'aide de la console Administration de BizTalk, un message d'erreur similaire à celui indiqué ci-après est généré :  
  
```  
Failed to execute action 'Stop'.  
------------------------------  
ADDITIONAL INFORMATION:  
A transport-level error has occurred when sending the request to the server. (provider: TCP Provider, error: 0 - An existing connection was forcibly closed by the remote host.) (Microsoft SQL Server, Error: 10054)  
```  
  
 Ce problème peut se produire si les conditions suivantes sont remplies :  
  
-   La console Administration de BizTalk est ouverte.  
  
-   La base de données de gestion BizTalk est installée sur une instance mise en cluster de SQL Server.  
  
-   L'instance mise en cluster de SQL Server est basculée.  
  
-   Une fois le basculement terminé, vous tentez d'arrêter une instance en cours d'exécution d'une orchestration à l'aide de la console Administration de BizTalk.  
  
##### <a name="cause"></a>Cause  
 La console Administration de BizTalk gère une connexion à la base de données de gestion [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Lorsque la connexion à la base de données de gestion [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est interrompue lors du basculement, certaines tâches de gestion peuvent retourner une erreur « Échec de connexion » ou « Échec de l'exécution » tant que la console n'a pas été fermée, puis rouverte.  
  
##### <a name="resolution"></a>Résolution  
 Fermez, puis réouvrez la console Administration de BizTalk. Une fois rouverte, la console établit une nouvelle connexion à la base de données de gestion [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] spécifiée.  
  
#### <a name="windows-group-names-that-were-previously-deleted-do-not-have-access-to-the-biztalk-server-databases"></a>Les noms de groupe Windows précédemment supprimés n'ont pas accès aux bases de données BizTalk Server  
  
##### <a name="problem"></a>Problème  
 Si, lors de la réinstallation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous utilisez un nom de groupe Windows qui a été précédemment supprimé, ce groupe n'aura pas accès aux bases de données BizTalk Server.  
  
##### <a name="cause"></a>Cause  
 La suppression d'un groupe Windows suivie de la création d'un groupe portant le même non génère un nouveau SID (Security Identifier) pour ce groupe. Cependant, l'ancien SID est toujours mis en cache dans SQL Server, ce qui empêche le nouveau groupe Windows de se connecter à SQL Server.  
  
##### <a name="resolution"></a>Résolution  
 Lorsque vous supprimez le groupe Windows, vous devez également supprimer la connexion SQL Server de celui-ci.  
  
#### <a name="biztalk-administrator-cannot-start-the-biztalk-server-administration-console"></a>L'administrateur BizTalk ne parvient pas à démarrer la console Administration de BizTalk Server  
  
##### <a name="problem"></a>Problème  
 Un administrateur BizTalk (membre du groupe Windows des administrateurs BizTalk) peut ne pas parvenir à ouvrir la console Administration de BizTalk Server s'il n'est pas membre du groupe des administrateurs Windows sur l'ordinateur local.  
  
##### <a name="cause"></a>Cause  
 Ce problème peut se produire si vous avez réinstallé ou reconfiguré BizTalk Server. Cela est dû au fait que SQL Server utilisait des ID de sécurité mis en cache.  
  
##### <a name="resolution"></a>Résolution  
 Ajoutez temporairement l'administrateur BizTalk au groupe des administrateurs Windows local sur l'ordinateur local. Après avoir ouvert la console Administration de BizTalk Server, supprimez-le.  
  
#### <a name="cannot-start-a-host-instance-on-a-remote-computer"></a>Impossible de démarrer une instance d'hôte sur un ordinateur distant  
  
##### <a name="problem"></a>Problème  
 Lorsque vous créez une instance d’hôte BizTalk sur un ordinateur distant, vous pouvez voir l’erreur suivante lorsque vous démarrez l’instance d’hôte BizTalk : « Échec de la démarrer en raison de l’échec d’ouverture de session ».  
  
##### <a name="cause"></a>Cause  
 Cette erreur peut se produire si vous avez entré des informations d'identification non valides pour le compte de service sous lequel l'instance d'hôte BizTalk s'exécute, ou si le compte de service ne dispose pas des droits de connexion en tant que service.  
  
##### <a name="resolution"></a>Résolution  
 Attribuez le droit de connexion en tant que service au compte de service de l'ordinateur distant avant de démarrer l'instance d'hôte BizTalk. Cela s'effectue automatiquement sur un ordinateur local, mais doit se faire manuellement sur un ordinateur distant.  
  
#### <a name="creating-or-configuring-a-host-instance-on-an-x64-computer-with-the-32-bit-only-option-selected-fails"></a>Échec de la création ou de la configuration d'une instance d'hôte sur un ordinateur X64 avec l'option 32 bits seulement sélectionnée  
  
##### <a name="problem"></a>Problème  
 Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], la création d'une instance d'hôte BizTalk sur un ordinateur X64 peut échouer lorsque l'option 32 bits seulement (option par défaut) est sélectionnée.  
  
 Dans le gestionnaire de configuration de BizTalk Server, lorsque vous configurez le composant d'exécution de BizTalk Server sur un ordinateur X64, le fait de créer une instance d'hôte isolée ou de type In-process alors que l'option 32 bits seulement est sélectionnée risque de faire échouer le démarrage du service.  
  
##### <a name="cause"></a>Cause  
 Unknown  
  
##### <a name="resolution"></a>Résolution  
 Le problème est aléatoire. Réessayez de créer ou de configurer l'hôte, ou désélectionnez l'option 32 bits seulement.  
  
#### <a name="host-instance-deletion-does-not-clear-registry-information"></a>La suppression de l'instance d'hôte Host n'efface pas les informations de registre  
  
##### <a name="problem"></a>Problème  
 Si vous n'avez pas la qualité d'administrateur sur l'ordinateur local, un message d'erreur indiquant que l'accès est refusé s'affiche lorsque vous supprimez un hôte de type In-process ou isolé. Vous pouvez supprimer l'hôte de force. Toutefois, cette méthode n'efface pas toutes les informations de registre associées.  
  
##### <a name="cause"></a>Cause  
 La suppression des informations de registre associées à une instance d'hôte requiert des privilèges d'administrateur.  
  
##### <a name="resolution"></a>Résolution  
 Connectez-vous en tant que compte d'administrateur local avant de supprimer l'hôte afin de supprimer également les informations de registre associées.  
  
#### <a name="cannot-delete-a-messagebox-database"></a>Impossible de supprimer une base de données MessageBox  
  
##### <a name="problem"></a>Problème  
 Vous ne parvenez pas à supprimer une base de données MessageBox. L'échec de la suppression peut être dû à l'un des problèmes suivants :  
  
-   L'intervalle d'actualisation du cache n'a pas expiré.  
  
-   La base de données MessageBox contient des instances incomplètes.  
  
 Si l’intervalle d’actualisation du cache n’a pas encore expiré, le message d’erreur suivant s’affiche en cas d’échec de la suppression : « MessageBox ne peut pas être supprimé, car il pourrait être travail restant dans la MessageBox. Veuillez vous assurer qu’il existe des instances incomplètes n’y a plus dans la MessageBox, puis réessayez. »  
  
##### <a name="cause"></a>Cause  
 L'intervalle d'actualisation du cache doit expirer entre le moment où vous désactivez la publication des nouveaux messages dans la base de données MessageBox et celui où vous supprimez la base de données. Par défaut, l’intervalle d’actualisation du cache est de 60 secondes.  
  
##### <a name="resolution"></a>Résolution  
 Pour supprimer une base de données MessageBox, vous devez d'abord désactiver la publication des nouveaux messages de celle-ci, puis patienter jusqu'à l'expiration de l'intervalle d'actualisation du cache.  
  
 Si la base de données MessageBox contient des instances de service incomplètes, le message d’erreur suivant s’affiche : « Impossible de supprimer la MessageBox car elle peut encore contenir des instances incomplètes. Assurez-vous qu'elle ne comporte plus aucune instance inachevée et recommencez. »  
  
 Vous pouvez afficher les instances de service incomplètes dans la base de données MessageBox à l'aide de la page Hub du groupe de la console Administration de BizTalk Server. Pour plus d’informations sur l’affichage de l’état des instances de service dans la page Hub du groupe, consultez [comment rechercher des Instances de Service suivies](../core/how-to-search-for-tracked-service-instances.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage](../core/troubleshooting.md)
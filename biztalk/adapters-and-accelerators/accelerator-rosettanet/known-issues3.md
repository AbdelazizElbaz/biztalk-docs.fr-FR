---
title: "Problèmes connus avec RosettaNet accelerator dans BizTalk Server | Documents Microsoft"
description: "Consultez les problèmes connus et solutions avec notification 0 a 1 Échec, BAM, installation et configuration de plus de BTARN dans BizTalk Server"
caps.latest.revision: "11"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 335eb3c9-b565-470f-b69c-2a771ef8b476
ms.author: mandia
ms.openlocfilehash: bbb7ddc2028383f8ac346e7876459f322d2dd96b
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="known-issues"></a>Problèmes connus
Cette section contient des informations utiles qui peuvent vous aider à éviter les erreurs avec [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]. Les problèmes connus sont regroupées dans les domaines suivants :  
  
-   Notification 0 a 1 de défaillance  
  
-   BAM (Business Activity Monitoring)  
  
-   Installation et Configuration  
  
-   Divers  
  
## <a name="0a1-notification-of-failure"></a>Notification 0 a 1 de défaillance  
  
### <a name="btarn-does-not-perform-cross-field-validation-for-the-cidx-process-configuration-property-and-the-0a1-agreement-property"></a>BTARN n’effectue pas de validation de champ croisé pour la propriété de configuration de processus CIDX et les propriétés de l’accord 0 a 1  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]ne vous empêche pas de la définition de la propriété « Standard » pour un profil de configuration de processus sur « CIDX », une fois que vous avez défini la propriété « contrat 0 a 1 » pour un accord à l’aide de ce profil pour « 0 a 1 », même si un CIDX ne prend pas en charge les contrats de 0 a 1.  
  
## <a name="business-activity-monitoring"></a>Analyse BAM (Business Activity Monitoring)  
  
### <a name="duplicate-column-data-appears-in-the-business-activity-monitoring-reports"></a>Données de la colonne en double s’affiche dans les rapports d’analyse BAM  
 Les colonnes ActivityID et le PIPInstanceID dans les rapports Web d’activités BAM contiennent le même contenu. Ces données reflètent précisément l’identificateur d’instance de processus PIP (Partner Interface). L’ID d’activité utilise cette valeur pour la corrélation interne. Vous pouvez ignorer ce message.  
  
### <a name="empty-data-columns-in-the-business-activity-monitoring-web-reports"></a>Colonnes de données vide dans les rapports Web de surveillance des bas  
 Les rapports d’analyse BAM (Business Activity) Web ne contiennent pas de données pour le processus de message 0 a 1. Les colonnes de message 0 a 1 dans les rapports Web sont codés en dur avec « A été initiée la 0 a 1 ».  
  
## <a name="installation-and-configuration"></a>Installation et Configuration  
  
### <a name="groups-and-users-in-either-the-biztalk-application-users-group-and-the-biztalk-server-administrators-group-must-be-in-the-same-domain"></a>Groupes et utilisateurs dans le groupe d’utilisateurs d’applications BizTalk et sur le groupe d’administrateurs BizTalk Server doivent être dans le même domaine  
 [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]prend en charge l’ajout d’un groupe pour le groupe d’utilisateurs d’applications BizTalk ou le groupe Administrateurs BizTalk Server. Toutefois, les comptes d’utilisateur individuels et les groupes qui appartiennent au groupe utilisateurs d’applications BizTalk ou au groupe d’administrateurs BizTalk Server doivent faire partie du même domaine.  
  
### <a name="uninstallation-of-btarn-fails-if-biztalk-server-is-removed-first"></a>La désinstallation de BTARN échoue si BizTalk Server est supprimé en premier  
 Si vous supprimez BizTalk Server avant de supprimer [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] processus de suppression échoue sans erreurs. Pour résoudre ce problème, réinstaller et reconfigurer BizTalk Server et ensuite supprimer [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].  
  
### <a name="distributed-deployment-requires-a-domain-controller"></a>Déploiement distribué nécessite un contrôleur de domaine  
 Déploiement [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] dans un environnement multiserveur nécessite un contrôleur de domaine, par exemple, lorsque vous avez installé [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] sur un serveur et le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] bases de données utilisées pour la configuration sur un autre serveur.  
  
### <a name="custom-pip-configurations-are-not-supported"></a>Les configurations PIP personnalisées ne sont pas pris en charge.  
 La version actuelle de [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ne prend pas en charge la configuration des adresses PIP avec des éléments personnalisés ou d’autres informations standard non RosettaNet.  
  
### <a name="btarn-automatically-starts-the-single-sign-on-service"></a>BTARN démarre automatiquement le service d’authentification unique  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]démarre automatiquement le Single Sign-On (SSO) dans un événement lorsque [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] requiert alors que le service d’authentification unique n’est pas en cours d’exécution.  
  
### <a name="the-configuration-program-will-not-remove-btarn-virtual-directories-from-the-excluded-paths-list-when-webapps-is-not-configured-for-the-default-web-site"></a>Le programme de configuration ne supprime pas les répertoires virtuels de BTARN de la liste de chemins d’accès exclus lorsque les applications Web n’est pas configuré pour le site Web par défaut  
 Si vous annulez la configuration un [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] installation dans lequel le dossier virtuel d’application Web a été configuré pour être un serveur SharePoint, pas Site Web par défaut, après l’annulation de configuration vous devrez supprimer manuellement le btarnapp fait et btarnhttpreceive virtuel répertoires à partir de la liste des chemins d’accès exclus dans le site d’Administration centrale de SharePoint. Cela se produit parce que lorsque vous configurez le dossier virtuel d’application Web à SharePoint Server, vous devez ajouter manuellement des btarnapp fait et btarnhttpreceive à la liste de chemins d’accès exclus. Le programme de configuration ne sera pas en mesure de les supprimer automatiquement dans la liste de chemins d’accès exclus.  
  
## <a name="miscellaneous"></a>Divers  
  
### <a name="btarn-will-receive-messages-encrypted-in-either-encryption-algorithm"></a>BTARN reçoit les messages chiffrés dans un algorithme de chiffrement  
 Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] réception pipeline reçoit et déchiffre un message, même si le protocole est utilisé pour chiffrer le message et le paramètre de codage dans ce champ ne correspondent pas. Par conséquent, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] reçoit des messages chiffrés dans RC2-40 ou 3DES.  
  
### <a name="btarn-requires-a-signal-in-a-single-action-synchronous-scenario"></a>BTARN requiert un signal dans un scénario synchrone action unique  
 Dans un scénario synchrone action unique, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] toujours attend et génère des signaux. Ce comportement est différent de la spécification de RosettaNet un signal peut ou ne peut pas être nécessaire dans un scénario synchrone action unique. Si [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] est un répondeur, il génère toujours un signal en réponse à un message à partir de l’initiateur. Si [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] est un initiateur, il attend toujours un signal du récepteur. Si [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ne reçoit pas d’un signal, il expire après l’intervalle spécifié dans le `Time To Perform` propriété dans les paramètres de configuration de processus et il génère un message 0 a 1.  
  
### <a name="btarn-supports-utf-16-in-received-messages"></a>BTARN prend en charge UTF-16 dans les messages reçus  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]reçoit et traite les messages qui ont un jeu de caractères UTF-16. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]envoie des messages avec un jeu de caractères UTF-8.  
  
### <a name="namespaces-must-be-stripped-from-response-messages-mapped-from-request-messages"></a>Espaces de noms doivent être supprimés à partir de messages de réponse mappés à partir de messages de demande  
 Si vous utilisez le Mappeur BizTalk dans le processus privé d’un scénario de double action, le Mappeur BizTalk ajoute des espaces de noms à des balises d’élément dans les instances de message de réponse mappés à partir de messages de demande. Ces espaces de noms provoquent un échec dans le pipeline d’envoi. Vous devez supprimer ces espaces de noms. Pour ce faire, utilisez l’exemple HeaderHelper. Pour plus d’informations, consultez [Orchestration Double Action PIPAutomation &#91; RN3 &#93; ](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md) et [étape 4 : créer le projet HeaderHelper &#91; RN3 &#93; ](../../adapters-and-accelerators/accelerator-rosettanet/step-4-creating-the-headerhelper-project.md).  
  
### <a name="changing-uri-settings-requires-iisreset"></a>Modification des paramètres d’URI requiert IISRESET  
 Lorsque vous exécutez le programme d’installation, vous définissez les paramètres de l’URI que les pages .aspx de réception et d’envoi utilisent et les paramètres de l’URI de la réception et les adaptateurs d’envoi. Vous devez modifier ces paramètres si vous modifiez le nom de l’ordinateur qui les pages .aspx ou les adaptateurs sont installés sur. Vous pouvez modifier ces paramètres en exécutant de nouveau le processus de configuration, mais cela nécessite la réinitialisation de tous les paramètres de configuration. Vous pouvez modifier les paramètres URI uniquement en modifiant les clés de Registre associées (`AsyncReceivePortURI`, `RNIFSenderURI`, et `SyncReceivePortURI`). Après avoir modifié l’un de ces paramètres de Registre, vous devez exécuter IISRESET pour que les modifications prennent effet. C’est parce que [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] met en cache les paramètres de son utilisation. Après l’exécution de IISRESET, vous devez également redémarrer les services BizTalk.  
  
### <a name="btarn-does-not-enforce-restrictions-on-rnif-v11-enumerations"></a>BTARN n’impose pas de restrictions sur les énumérations RNIF v1.1  
 La spécification de Framework RNIF (RosettaNet Implementation) v1.1 indique les restrictions sur certaines énumérations de schéma RNIF. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]ne pas appliquer ces restrictions et ne valide pas par rapport à ces restrictions. Les restrictions ne s’appliquent pas à RNIF v2.01.  
  
 Cela est vrai pour les éléments d’en-tête de service suivants :  
  
-   `GlobalBusinessActionCode`  
  
-   `GlobalPartnerClassificationCode`  
  
-   `GlobalBusinessServiceCode`  
  
-   `GlobalProcessCode`  
  
-   `GlobalProcessIndicatorCode`  
  
-   `VersionIdentifier`  
  
### <a name="performancecontrolrequest-parameters-will-not-override-default-process-configuration-settings"></a>Les paramètres PerformanceControlRequest ne remplacent pas les paramètres de configuration de processus par défaut  
 Peuvent contenir des messages entrants `PerformanceControlRequest` paramètres dans l’en-tête de service. Ces paramètres incluent les valeurs pour les paramètres de délai de temps de temps pour l’accusé de réception (réception) et l’heure à effectuer, comme défini dans les paramètres de configuration de processus définis dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]ne pas définir de façon dynamique les retards d’heure selon le `PerformanceControlRequest` paramètres dans le message entrant. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]accepte toujours les délais PIP les valeurs par défaut définies dans les paramètres de configuration de processus. Il suit la spécification du Framework RNIF (RosettaNet Implementation) v1.1.  
  
### <a name="the-pip-name-and-pip-version-of-double-action-messages-are-case-sensitive"></a>Le nom du PIP et la version PIP double action messages respectent la casse  
 Si le nom du PIP et la version PIP d’un message de réponse ont une casse différente, que les valeurs correspondantes de la demande de double action d’origine d’un message, l’initiateur [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] rejette le message de réponse comme non valide et renvoie une exception au répondeur.  
  
### <a name="btarn-does-not-support-changing-agreement-settings-while-there-are-active-processes"></a>BTARN ne prend pas en charge la modification des paramètres de contrat s’il existe des processus actifs  
 Modifications apportées aux propriétés de l’accord seront applique dès que vous cliquez sur **appliquer** ou **OK** pour les accepter. Après avoir modifié un accord, toute nouvelle activité dans un processus déjà en cours d’exécution ou tout nouveau processus impliquant cet accord utilisera les propriétés modifiées. S’il existe un processus en cours d’exécution lorsque vous avez modifié l’accord, il ont déjà été utilisé les propriétés d’accord pour un message. Les nouveaux messages pour ce processus utilisera les nouveaux paramètres d’accord, ce qui peuvent générer des résultats imprévisibles. Il est recommandé de modifier les paramètres de l’accord lorsqu’il n’y a aucun processus en cours d’exécution.  
  
### <a name="btarn-will-not-perform-cross-field-validation-after-changes-to-a-process-configuration-profile"></a>BTARN n’effectuera pas de validation de champ croisé après les modifications apportées à un profil de configuration de processus  
 Lorsque vous créez un profil de configuration de processus et ensuite créer un accord, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] effectue la validation de champ croisé pour vous assurer que les propriétés de l’accord et le profil sont compatibles. Par exemple, il vérifie que pour un profil dont la propriété Standard est définie sur « CIDX », les propriétés de l’accord 0 a 1 de l’accord sont définie à « Aucune 0 a 1 ». Toutefois, si vous modifiez un profil de configuration de processus après avoir créé un accord, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] n’effectue pas de validation de champ croisé. Si vous modifiez la propriété Standard de « RosettaNet » à « CIDX », [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ne vérifie pas que les propriétés de l’accord 0 a 1 de l’accord sont définie à « Aucune 0 a 1 ».  
  
### <a name="errors-will-result-if-all-orchestrations-are-not-started"></a>Erreurs se produira si toutes les orchestrations ne sont pas démarrées.  
 Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] programme d’installation installe les neuf orchestrations. Pour [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pour traiter correctement les messages, vous devez lier, inscrire et démarrer neuf toutes ces orchestrations avant de lancer le traitement. Pour plus d’informations, consultez les rubriques « Gestion d’Orchestration dans BizTalk Explorer » ou « Gestion des Orchestrations » dans l’aide de BizTalk Server.  
  
### <a name="rnifreceiveaspx-does-not-remove-the-mime-bottom-boundary-from-a-message"></a>Fichier RNIFReceive.aspx ne supprime pas la limite inférieure MIME d’un message  
 Lorsque la page RNIFReceive.aspx reçoit un message à partir d’une page de fichier RNIFSend.aspx d’un partenaire, le message inclut un en-tête MIME et une limite de haut et bas MIME, un nombre à base 64. Fichier RNIFSend.aspx ajoute l’en-tête et les limites de message pour la transmission de RNIF. Fichier RNIFReceive.aspx doit supprimer l’en-tête MIME et les limites du message avant d’envoyer le message pour le processus public. Fichier RNIFReceive.aspx supprime l’en-tête MIME et la limite supérieure, mais elle ne supprime pas la limite inférieure. La présence de la limite inférieure n’affecte pas le traitement du message dans le processus public.  
  
### <a name="btarn-does-not-support-a-case-sensitive-configuration-of-sql-server-databases"></a>BTARN ne prend pas en charge une configuration de la casse des bases de données SQL Server  
 Si vous apportez [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] bases de données et les objets de base de données qui respecte la casse, le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion ne peut pas trouver des ressources de base de données et lève une exception. Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] bases de données et les objets de base de données doivent être pas la casse.  
  
### <a name="all-queries-in-database-maintenance-scripts-should-be-written-for-utc-time"></a>Toutes les requêtes dans les scripts de maintenance de base de données doivent être écrit pour l’heure UTC  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] bases de données utilisent l’heure UTC (Universal Time Coordinate), afin que les requêtes que vous créez pour maintenir une de ces bases de données doit être écrites pour l’heure UTC. Par exemple, si votre script de maintenance à utiliser le `GetDate()` de commande, vous devez le remplacer par `GetUTCDate()`.  
  
### <a name="a-publicresponder-orchestration-will-reject-a-duplicate-request-action-message"></a>Une orchestration PublicResponder rejette un message d’action demande dupliquée  
 Lorsqu’un `PublicResponder` orchestration (PublicResponderV11.odx) reçoit un message d’action de demande en double, il consigne un avertissement dans le journal des événements et puis rejette le message. Si un message dupliqué est reçu après que l’orchestration du répondeur est terminée, BizTalk Server s’arrête le message, car aucun abonnement.  
  
### <a name="transmission-errors-will-not-be-shown-in-bam-if-the-public-process-has-stopped"></a>Erreurs de transmission seront affichera pas dans l’analyse BAM si le processus public s’est arrêté  
 Si une erreur de transmission se produit lorsqu’une orchestration de processus publics traite le message final, le journal des événements et du fonctionnement affichent l’erreur, mais n’est pas le cas de l’analyse BAM. BAM ne peut pas afficher le message parce que l’orchestration a arrêté.  
  
### <a name="the-pipelineexe-tool-cannot-be-used-to-debug-a-btarn-receive-pipeline"></a>L’outil pipeline.exe ne peut pas être utilisé pour déboguer un BTARN pipeline de réception  
 Si vous souhaitez déboguer un pipeline de réception, vous devez créer un port hébergeant le pipeline. Vous ne pouvez pas déboguer à l’aide de l’outil pipeline.exe par BizTalk Server.  
  
### <a name="an-error-may-be-generated-for-a-retried-message-that-is-successfully-processed-after-the-orchestration-finishes"></a>Une erreur peut être générée pour un message de nouvelle tentative qui a été correctement traité une fois l’orchestration terminée  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]utilise des orchestrations pour représenter des flux de processus. Dans certains cas, dans lequel plusieurs messages de nouvelle tentative sont retentées, l’orchestration peut terminer correctement avant l’arrivée d’un message de nouvelle tentative dans la BizTalk MessageBox. Lorsque ce comportement survient, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] génère un message d’erreur correspondant » s’est terminée mais ignorées ». Vous devez examiner votre application de métier (LOB) pour déterminer si le processus est terminé ou non. Si l’application métier indique l’exécution réussie, vous pouvez ignorer le message « terminé mais ignoré ».  
  
### <a name="an-xml-file-exported-from-trackingxls-may-have-incorrect-fields"></a>Un fichier XML exporté à partir de tracking.xls peut avoir des champs incorrects  
 Lorsque vous définissez de nouveaux affichages de suivi dans un fichier XLS de suivi et exportez un fichier XML à partir du fichier XLS de suivi, certains des noms de champ seront légèrement modifiées. Pour corriger ce problème, vérifiez les champs dans votre suivi personnalisé fichier XML dans le champ tracking.xml standard installés par [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] le programme d’installation.  
  
### <a name="rnif-11-service-header-schema-for-signals-and-responses-may-need-modification"></a>Schéma d’en-tête RNIF 1.1 service pour les signaux et les réponses peut-être nécessiter des modifications  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]est fourni à tous les schémas d’en-tête RosettaNet prêtes à l’emploi. Certaines implémentations utilisent les nœuds d’Action et le contrôle de Signal différemment des autres, comme décrit ci-dessous.  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]emploi fourni l’élément de contrôle de Signal comme indiqué ci-dessous. Notez que le même peut être vrai pour l’élément de contrôle de l’Action.  
  
```  
<!ELEMENT SignalControl (  
          InstanceIdentifier,  
          PartnerRoute,  
          SignalIdentity,  
          inResponseTo)>  
```  
  
 Si votre solution requiert cette séquence, vous n’avez pas besoin rien à faire.  
  
 D’autres implémentations, utilisent quant à eux, le code suivant :  
  
```  
<!ELEMENT SignalControl (  
          inResponseTo,  
          InstanceIdentifier,  
          PartnerRoute,  
          SignalIdentity)>  
```  
  
 Si votre solution requiert cette séquence, reportez-vous à la base de connaissances 889523. Cette mise à jour logicielle change le schéma XML correspondant. Notez que cette mise à jour affecte uniquement les processus RNIF 1.1.  
  
### <a name="pipautomationgetaction-sql-stored-procedure-needs-update"></a>Procédure stockée SQL de PipAutomationGetAction nécessite la mise à jour  
 Vous devez mettre à jour de l’instruction SQL PipAutomationGetAction une procédure stockée à verrouiller des enregistrements uniques. Supprimer les lignes suivantes :  
  
```  
IF @@ERROR <> 0  
    UPDATE MessagesToLOB SET Delivered = -1 WHERE MessageID = @tempGUID  
```  
  
 La procédure stockée de PipAutomationGetAction correcte est la suivante :  
  
```  
CREATE PROCEDURE PipAutomationGetAction  
AS  
 SET TRANSACTION ISOLATION LEVEL READ COMMITTED  
BEGIN TRANSACTION  
DECLARE @tempGUID nvarchar(36)  
SELECT TOP 1 @tempGUID = MessageID FROM MessagesToLOB WITH (READPAST,UPDLOCK,ROWLOCK)  
   WHERE Delivered = 0 AND MessageCategory = 10  
  ORDER BY TimeCreated  
  SELECT PIPInstanceID,DestinationPartyName,SourcePartyName,PIPCode,PIPVersion, ServiceContent FROM MessagesToLOB  
   WHERE MessageID = @tempGUID  
For xml auto  
UPDATE MessagesToLOB SET Delivered = 1 WHERE MessageID = @tempGUID  
 COMMIT TRANSACTION  
GO  
```  
  
### <a name="you-can-customize-aspx-code-to-return-the-error-description"></a>Vous pouvez personnaliser le code aspx pour retourner la description d’erreur  
 Si vous avez besoin pour se connecter ou envoyer une description de l’erreur, vous pouvez personnaliser le code aspx pour que le texte retourné dans la réponse. Pour ce faire, utilisez HttpResponse.Status (qui est un objet de réponse de la demande d’intrinsèque asp) ou HttpWebResponse.StatusDescription (qui est retournée par le [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] de l’appel à la méthode de l’objet HttpWebRequest GetResponse). Pour retourner les valeurs de retour à partir d’un des objets de la réponse applicable, définissez la valeur Response.Status similaire à la façon dont Response.StatusCode est défini dans le code aspx qui est fourni avec [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].  
  
### <a name="rnif-11-messages-cannot-be-read-in-plain-text-from-non-repudiation-tables-if-the-encoding-method-is-set-to-base64"></a>Impossible de lire les messages RNIF 1.1 en texte brut à partir des tables de non répudiation si la valeur de la méthode de codage en Base64  
 Cela se produit uniquement si la valeur de la méthode de codage en Base64. Les messages peuvent être lus en texte clair à partir des tables de non répudiation si méthode de codage a la valeur quoted printable ou 8 bits. Vous devez enregistrer le fichier de message avec l’extension de *.eml, puis ouvrez-le à l’aide d’Outlook Express pour lire le message et Outlook Express décode le message pour vous. Vous pouvez également utiliser le code ci-dessous pour lire les messages codé en Base64 à partir des tables de non répudiation.  
  
```  
byte[] textBytes = Convert.FromBase64String(txtEncodedText.Text);  
string plainText = Encoding.UTF8.GetString(textBytes);  
txtOutput.Text = plainText;  
```  
  
## <a name="see-also"></a>Voir aussi  
[Dépannage et problèmes connus](troubleshooting-and-known-issues-in-rosettanet.md)
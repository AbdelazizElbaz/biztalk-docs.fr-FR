---
title: "La réparation et le dépannage de la nouvelle soumission de messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, Message Repair and New Submission
- Message Repair and New Submission, troubleshooting
ms.assetid: bb07a286-6f02-4639-b5fa-a3647e356ac8
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d341a7f03c70e1ddcd242d7804b162338798e94
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="message-repair-and-new-submission-troubleshooting"></a>Réparation de message et le dépannage de la nouvelle soumission
## <a name="a-repaired-message-cannot-be-submitted-if-the-envelope-schema-is-not-deployed"></a>Impossible de soumettre un message réparé si le schéma d’enveloppe n’est pas déployé.  
  
### <a name="symptom"></a>Symptôme  
 Lorsque vous essayez d’envoyer un message que vous avez réparé, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] publie le message suivant :  
  
 « Échec de l’adaptateur envoyer le message pour le port d’envoi « http://mrsrtest:80/StsWebReceive/default.aspx?PartnerId=Unparsed & FolderType = MessagesInbox ». Il est retransmis après l’intervalle de nouvelle tentative spécifié pour ce Port d’envoi. Détails : « 80131600 ». Pour plus d’informations, consultez le centre d’aide et Support à [http://go.microsoft.com/fwlink/?LinkId=142493](http://go.microsoft.com/fwlink/?LinkId=142493).  
  
### <a name="possible-cause"></a>Cause possible  
 Le schéma d’enveloppe n’est pas déployé. Cela est vrai pour n’importe quel MT*xxx* message ou tout message qui a échoué à l’analyse.  
  
### <a name="solution"></a>Solution  
 Déployer un schéma d’enveloppe pour chaque schéma de message que vous utilisez (\<lecteur\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack \SWIFT Messages\ A4SWIFT-SRG\<version\>\Category n\MTxxx.xsd) et pour le schéma d’enveloppe non analysé (\<lecteur\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT \<version\> Message Pack \ SWIFT Messages\ A4SWIFT-SRG\<version\>\ Message\EnvelopeUnparsedMessage.xsd non analysée). Pour plus d’informations, consultez [déploiement des schémas A4SWIFT](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md).  
  
## <a name="you-cannot-submit-a-fixed-unparsed-message-from-a-mrsr-site-library-named-other-than-unparsed"></a>Vous pouvez envoyer un message non analysé fixe d’une bibliothèque de site MRSR nommé autre que « Unparsed »  
  
### <a name="symptom"></a>Symptôme  
 Lorsque vous essayez d’envoyer un message non analysé que vous avez résolu à partir d’une bibliothèque de documents MRSR site qui n’est pas nommée « Unparsed », l’opération échoue.  
  
### <a name="possible-cause"></a>Cause possible  
 A4SWIFT a été impossible d’envoyer un message à partir d’une bibliothèque qui n’est pas nommé « Unparsed ». Si vous avez une bibliothèque de documents « Unparsed » existante dans le site MRSR avant d’installer cette MRSR (message) fonction, le programme d’installation A4SWIFT créera une bibliothèque pour les messages non analysées intitulée « Unparsed » avec un suffixe. Lorsqu’il reçoit un message A4SWIFT n’a pas pu analyser, il achemine le message à cette bibliothèque qu’il a créées. Toutefois, lorsque vous essayez d’envoyer un message à partir de cette bibliothèque, l’opération échoue.  
  
### <a name="solution"></a>Solution  
 Supprimer la fonctionnalité MRSR, supprimer la bibliothèque non analysée, puis réinstallez la fonctionnalité MRSR.  
  
## <a name="cannot-loop-back-a-message-in-a-two-stage-workflow"></a>Ne peut pas renvoyer en boucle un message dans un flux de travail de deux étapes  
  
### <a name="symptom"></a>Symptôme  
 Si vous le rejetez un message pendant la phase de réparation d’un flux de travail qui a uniquement une étape de création et une phase de réparation, la soumission échoue. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]achemine le message vers la MessageBox et publie le message d’erreur suivant :  
  
 « Impossible de réinitialiser à la première étape dans le flux de travail. »  
  
### <a name="possible-cause"></a>Cause possible  
 Boucle de message n’est pas pris en charge pour un workflow qui a uniquement une étape de création et une phase de réparation.  
  
### <a name="solution"></a>Solution  
 Ajouter une autre étape du flux de travail de deux étapes, ou annuler l’envoi.  
  
## <a name="cannot-open-a-message-in-the-repair-inbox-in-mrsr"></a>Impossible d’ouvrir un message dans la boîte de réception réparation MRSR  
  
### <a name="symptom"></a>Symptôme  
 Lorsque vous essayez d’ouvrir un message dans la boîte de réception réparation MRSR, le message d’erreur suivant s’affiche dans une fenêtre contextuelle :  
  
 « Impossible d’ouvrir de base de données demandée dans la connexion 'A4SWIFT'. La connexion échoue. Échec de la connexion pour l’utilisateur 'NT AUTHORITY\NETWORK SERVICE'.  
  
### <a name="possible-cause"></a>Cause possible  
 Le compte de connexion pour l’application web du service web A4SWIFT_MRSR sous lequel s’exécute est Service réseau, pas une variable locale ou un compte de domaine qui est membre du groupe utilisateurs d’A4SWIFT.  
  
### <a name="solution"></a>Solution  
 Modifier le compte de connexion pour l’application web du service web A4SWIFT_MRSR sous lequel s’exécute.  
  
##### <a name="to-change-the-login-account-for-the-web-application-that-the-a4swiftmrsr-web-service-runs-under"></a>Pour modifier le compte de connexion pour l’application web sous lequel le service web A4SWIFT_MRSR fonctionne  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Gestionnaire des services Internet (IIS)**.  
  
2.  Dans le Gestionnaire IIS, développez le  ***\<nom du serveur\>*  (ordinateur local)** nœud, la **Pools d’applications** nœud et le **Web Sites** nœud. Sous le nœud Sites Web, développez le **Site Web par défaut** nœud.  
  
3.  Sous le nœud de Site Web par défaut, cliquez sur **A4SWIFT_MRSR**, puis cliquez sur **propriétés**.  
  
4.  Dans la boîte de dialogue Propriétés de A4SWIFT_MRSR, notez le pool d’applications.  
  
5.  Dans la boîte de dialogue Gestionnaire des services Internet, sous le nœud Pools d’applications, cliquez sur le pool d’applications pour A4SWIFT_MRSR, puis cliquez sur **propriétés**.  
  
6.  Dans le \<nom du pool\> boîte de dialogue Propriétés, cliquez sur le **identité** Remarque. Si **prédéfini** est activé et **Service réseau** est sélectionnée, cliquez sur **Configurable**, entrez votre compte local ou de domaine, puis entrez votre mot de passe. Cliquez sur **OK**.  
  
## <a name="a-message-created-in-mrsr-site-on-a-localized-computer-is-not-processed"></a>Un message créé dans le site MRSR sur un ordinateur localisé n’est pas traité.  
  
### <a name="symptom"></a>Symptôme  
 Lorsqu’un utilisateur qui travaille sur une version anglaise d’A4SWIFT s’exécute sur une plateforme localisée crée un message dans une [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] écran MRSR et envoie le message avec succès, le message s’affiche à être consommés par le Message Repair et New Submission orchestration, mais n’a ne pas été correctement traité. Le message est envoyé à la boîte d’envoi, mais n’est pas récupéré par l’adaptateur BizTalk. Aucune erreur ou un avertissement n’est validée dans l’événement visionneuse, et il n’existe aucun enregistrement d’une instance d’orchestration en cours d’exécution dans l’outil HAT.  
  
### <a name="possible-cause"></a>Cause possible  
 Le chemin entré en tant que l’URI pour le service STS. La boîte d’envoi de réception emplacement contient le nom anglais, pas le nom localisé.  
  
### <a name="solution"></a>Solution  
 Modifier l’adresse URI pour le service STS. La boîte d’envoi emplacement de réception comme suit :  
  
1.  Dans la Console Administration de BizTalk Server 2009, développez le **groupe BizTalk**, **Applications**, et **BizTalk Application 1 nœuds**.  
  
2.  Cliquez sur **les emplacements de réception**.  
  
3.  Double-cliquez sur **STS.Outbox.Location**.  
  
4.  Dans la boîte de dialogue Propriétés de l’emplacement de réception, cliquez sur **configurer**.  
  
5.  Dans la boîte de dialogue Propriétés du Transport, remplacez la valeur de **SharePointSite URL** avec l’équivalent localisé.  
  
6.  Cliquez sur **OK**, puis cliquez sur **OK**.  
  
## <a name="removing-a-role-while-it-is-processing-a-message-results-in-incomplete-removal-of-documents-and-artifacts"></a>Suppression d’un rôle pendant le traitement d’un message généré dans la suppression incomplète de documents et des artefacts  
  
### <a name="symptom"></a>Symptôme  
 Lorsque vous supprimez un rôle dans le Client Web de profil, une boîte de dialogue est publiée, indiquant que tous les documents et les artefacts associés au rôle seront supprimés. Toutefois, le rôle n’est pas supprimé du service dans la Console de gestion d’A4SWIFT, et les dossiers de documents du rôle (boîte de réception et éléments envoyés) ne sont pas supprimées des MRSR. La partie, le port d’envoi et l’accord associé au rôle sont supprimés, et le profil du rôle est annulé.  
  
### <a name="possible-cause"></a>Cause possible  
 Un message est toujours dans la boîte de réception du rôle dans MRSR, et le message est ouvert dans son [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire.  
  
### <a name="solution"></a>Solution  
 Supprimez manuellement le message à partir de la boîte de réception du site MRSR, puis supprimez la bibliothèque de documents qui est associée au rôle qui vous ont été suppression. Fermer le formulaire et nouveau de supprimer le rôle.  
  
## <a name="message-processing-fails-as-a-result-of-an-error-in-the-bic-master-policy"></a>Traitement du message échoue en raison d’une erreur dans la stratégie BIC principale  
  
### <a name="symptom"></a>Symptôme  
 Quand vous envoyez un message pour le traitement, vous recevez l’erreur suivante :  
  
 « Une erreur s’est produite lors de l’exécution de la BicMasterPolicy. Vérifier la stratégie pour les valeurs valides. »  
  
### <a name="possible-cause"></a>Cause possible  
 Le nom SQL Server, nom de base de données BIC et valeur de la sécurité intégrée dans le fichier BIC_Master_Policy.xml  *\<lecteur\>*: \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \<version \> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base stratégies sont contenus dans des guillemets doubles. Pour activer la validation BIC, vous entrez ces chaînes dans le fichier BIC_Master_Policy.xml par défaut comme décrit dans [l’activation de Validation d’identificateur de Codes de la banque](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md).  
  
### <a name="solution"></a>Solution  
 Pour réparer la stratégie maître BIC, procédez comme suit :  
  
> [!NOTE]
>  Pour plus d’informations sur le déploiement de la stratégie de principal BIC, consultez [BRE, les règles de déploiement](../../adapters-and-accelerators/accelerator-swift/deploying-bre-rules.md).  
  
1.  Dans l’éditeur des règles d’entreprise, annuler le déploiement de la Version 1.0 de la BIC_Master_Policy et supprimez le BIC_Master_Policy.  
  
2.  Dans un éditeur de texte, tel que le bloc-notes, ouvrez BIC_Master_Policy.xml dans  *\<lecteur\>*: \Program Files\ Microsoft BizTalk Accelerator pour SWIFT \<version\> Pack\SWIFT de Message Messages\A4SWIFT-SRG\<version\>\Base stratégies. Supprimez les guillemets autour du nom de SQL Server et BIC nom de base de données intégré de valeur de sécurité.  
  
3.  Dans l’Assistant Déploiement du moteur de règles d’entreprise, importer BIC_Master_Policy.xml, puis déployez BIC_Master_Policy.xml.  
  
4.  Dans la console MMC Services, redémarrez le Service de mise à jour de moteur de règle et le Service hôte de réception BizTalk.  
  
## <a name="a4swift-will-not-be-able-to-process-an-unparsed-message-without-proper-database-permissions"></a>A4SWIFT ne sera pas en mesure de traiter un message non analysé sans les autorisations appropriées de la base de données  
  
### <a name="symptom"></a>Symptôme  
 Lorsque vous supprimez un message A4SWIFT ne peut pas analyser, A4SWIFT ne peut pas traiter le message, mais échoue avec une exception non interceptée.  
  
### <a name="possible-cause"></a>Cause possible  
 Il existe un problème d’autorisation de base de données. Le compte d’ouverture de session pour le service BizTalk, qui est HostSvc, par défaut n’est pas inclus dans les groupes administrateurs d’A4SWIFT et les utilisateurs d’A4SWIFT.  
  
### <a name="solution"></a>Solution  
 Ajoutez le compte d’ouverture de session pour le service BizTalk aux groupes administrateurs d’A4SWIFT et les utilisateurs d’A4SWIFT.  
  
## <a name="a-timeout-of-the-infopath-repair-form-can-result-in-two-copies-of-a-message-in-different-stages-of-the-repair-workflow"></a>Un délai d’attente du formulaire InfoPath réparation peut entraîner deux copies d’un message lors des différentes étapes du flux de travail de réparation  
  
### <a name="symptom"></a>Symptôme  
 Quand vous envoyez un message à partir d’un formulaire InfoPath (pour n’importe quelle étape du flux de travail), s’il existe une erreur dans l’envoi du formulaire, l’erreur peut entraîner deux copies du message. Un message est toujours dans la boîte de réception pour les étapes en cours, et l’autre message est dans la boîte de réception pour le rôle suivant dans le flux de travail. Toute tentative traiter ces messages entraîne les éléments suivants :  
  
-   Si vous envoyez le message à partir de la boîte de réception pour le rôle suivant du flux de travail, le message continue via le flux de travail.  
  
-   Si vous envoyez le message à partir de la boîte de réception pour le stade actuel une fois le message envoyé à partir de la boîte de réception de l’étape suivante a terminé le traitement, le message envoyé à partir de la boîte de réception en cours est suspendu avec un échec de routage.  
  
-   Si vous envoyez le message dans la boîte de réception pour l’étape actuelle avant la fin du message envoyé à partir de la boîte de réception de l’étape suivante du traitement, le message envoyé à partir de la boîte de réception pour l’étape actuelle s’affichera à la boîte de réception pour cette phase, et vous l’erreur suivante :  
    « La redéfinition des flux de travail pour la raison suivante : l’utilisateur n’est pas valide pour cette étape ou le message a été falsifié. »  
    Cette opération, si vous envoyez le message à partir de la boîte de réception pour l’étape suivante, le flux de travail pour qu’il est également réinitialisée. Il s’affichera à la boîte de réception pour l’étape actuelle et vous recevez l’erreur ci-dessus.  
  
### <a name="possible-cause"></a>Cause possible  
 Le formulaire InfoPath a envoyé le message à BizTalk Server via Microsoft Windows Sharepoint Services et d’un service Web personnalisé qui effectue des validations. Envoi d’un message s’effectue en plusieurs étapes, et ces étapes ne sont pas transactionnelles, étant donné que Windows Sharepoint Services n’est pas transactionnelle. Pour répondre à cette limitation, les orchestrations MRSR ont créé dans la logique de récupération pour détecter et résoudre des erreurs résultant de l’envoi du message. Les orchestrations MRSR toujours empêchent des messages en double envoyés à SWIFT.  
  
### <a name="solution"></a>Solution  
 Si cela se produit, vous devez récupérer le message qui est plu loin dans le flux de travail et effectuer des son flux de travail avant de tenter de traiter les autres messages qui se trouvent dans des étapes antérieures du flux de travail. Une fois que le message est plu loin dans le flux de travail a terminé le traitement, vous pouvez supprimer le second message (qui a été suspendu avec un échec de routage) comme vous le souhaitez.  
  
 Si le message est davantage le long dans le flux de travail a échoué avant que vous avez traité le deuxième message de traitement, vous devez à nouveau de réparer le message est plu loin dans le flux de travail de la réparation de formulaire InfoPath et envoyez-le. Autoriser à terminer le traitement, puis soumettez le second message. Une fois que le deuxième message a été suspendu, la supprimer.  
  
## <a name="a-new-submission-with-no-verify-stage-will-result-in-a-suspended-message"></a>Génère une nouvelle soumission avec aucune phase de vérification dans un message suspendu  
  
### <a name="symptom"></a>Symptôme  
 Quand vous envoyez un message dans un workflow qui n’a aucune phase de vérification, le message est suspendu.  
  
### <a name="possible-cause"></a>Cause possible  
 L’absence d’une étape de vérification des résultats dans un message suspendu si A4SWIFT_MRSRLastStage n’est pas défini sur Créer.  
  
### <a name="solution"></a>Solution  
 Utiliser un abonnement de A4SWIFT_MRSRLastStage == créer pour vous assurer que le message est correctement acheminé.  
  
## <a name="validation-of-message-results-a-parse-error-in-the-infopath-form-task-pane"></a>Validation du message entraîne une « erreur d’analyse » dans le volet de tâches de formulaire InfoPath  
  
### <a name="symptom"></a>Symptôme  
 Bouton de Message dans InfoPath volet formulaire affiche « Erreur d’analyse » sans aucune description de la validation.  
  
### <a name="solution"></a>Solution  
 Redémarrez le service web MRSR ou faire iisreset.  
  
## <a name="publishing-an-infopath-form-results-an-authorization-error"></a>Publication d’un formulaire InfoPath entraîne une erreur d’autorisation  
  
### <a name="symptom"></a>Symptôme  
 Publication d’un formulaire InfoPath donne erreur d’autorisation.  
  
### <a name="solution"></a>Solution  
 Remplacez le nom de l’ordinateur par localhost dans l’URL du site MRSR.  
  
## <a name="infopath-form-task-pane-shows-html-source-code"></a>Volet de tâches de formulaire InfoPath montre le code source HTML  
  
### <a name="symptom"></a>Symptôme  
 Volet de tâches de formulaire InfoPath montre le code source HTML au lieu de contrôles Web.  
  
### <a name="solution"></a>Solution  
 Accédez à **outils**-> **onglet sécurité** -> **Zone Internet**et activer **ouvrir un fichier en fonction du contenu pas sur l’extension** sous divers.  
  
## <a name="profile-web-client-website-results-an-authentication-error"></a>Site Web du Client Web profil entraîne une erreur d’authentification  
  
### <a name="symptom"></a>Symptôme  
 Site Web de profil Client Web affiche l’erreur d’authentification.  
  
### <a name="solution"></a>Solution  
 Exécutez le **BTSharePointAdapterWSAppPool** et **DefaultAppPoolApplication** -> et de pool dans Internet Information Services sous le compte d’administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage : problèmes et résolutions](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)
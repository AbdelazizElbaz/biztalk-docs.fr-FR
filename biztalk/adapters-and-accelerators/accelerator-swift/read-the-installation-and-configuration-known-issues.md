---
title: "L’installation et la configuration des problèmes connus de lecture | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c58d9dcb-7835-4181-a6cb-203c5d138e6a
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83bbeec3430f479d28502e818b9ead402278f9b1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="read-the-installation-and-configuration-known-issues"></a>Lecture de l’installation et la configuration des problèmes connus
  
## <a name="installing-over-terminal-server-creates-log-files-in-a-different-folder"></a>L’installation sur le serveur Terminal Server crée des fichiers journaux dans un dossier différent  
 Lorsque vous installez A4SWIFT via une connexion de Terminal Server, le programme d’installation d’A4SWIFT crée les fichiers journaux d’installation et de configuration dans le  *\<lecteur\>*: \Documents and Settings\\  *\<nom d’utilisateur\>*dossier de \Local Settings. Normalement, le programme d’installation crée ces fichiers dans le  *\<lecteur\>*: \Documents and Settings\\*\<nom d’utilisateur\>*\Local Dossier de Settings\Temp. Vous pouvez examiner ces fichiers journaux pour vous assurer que vos ordinateurs sont définis et configurés correctement.  
  
## <a name="silent-installation-is-not-recommended"></a>Installation sans assistance n’est pas recommandée.  
 Une installation sans assistance est pris en charge par le programme d’installation d’A4SWIFT, mais n’est pas recommandée en raison de la complexité des étapes de configuration supplémentaires sont nécessaires.  
  
## <a name="a4swift-setup-runs-with-the-installplatform-argument-that-overwrites-dlls-for-visualstudionet"></a>Le programme d’installation A4SWIFT s’exécute avec l’argument /InstallPlatform qui remplace la DLL pour VisualStudio.Net  
 Le programme d’installation A4SWIFT s’exécute toujours avec l’argument /InstallPlatform. Par conséquent, le programme d’installation A4SWIFT installe toujours msvcr71.dll mfc71u.dll, msvcp71.dll et atl71.dll, qui sont nécessaires pour [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. A4SWIFT le programme d’installation installe ces fichiers DLL dans le dossier %WINDIR%\System32, si les DLL sont déjà installés ou non.  
  
## <a name="canceling-a4swift-configuration-will-fail"></a>L’annulation d’A4SWIFT configuration échoue  
 En cliquant sur **Annuler** pendant A4SWIFT configuration n’est pas annulé configuration. Le processus de configuration se poursuit jusqu'à la fin.  
  
## <a name="after-unconfiguring-a4swift-you-cannot-reconfigure-in-the-same-instance-of-the-configuration-console"></a>Après avoir annulé la configuration d’A4SWIFT, vous ne pouvez pas reconfigurer dans la même instance de la console de Configuration  
 Si vous annulez la configuration d’A4SWIFT, ou un composant d’A4SWIFT, vous ne pouvez pas reconfigurer A4SWIFT ou ses composants sans tout d’abord fermer la console de Configuration d’A4SWIFT, puis de le rouvrir. Si vous ne le faites pas, certains champs de la console de Configuration seront grisées et vous ne serez pas en mesure de sélectionner des valeurs pour les.  
  
## <a name="configuration-of-a-web-components-only-installation-will-succeed-even-if-no-a4swift-database-exists"></a>Configuration d’une installation de composants uniquement Web réussira même si aucune base de données A4SWIFT n’existe  
 Si vous effectuez une installation personnalisée qui installe uniquement les composants Web pour la fonctionnalité de Message Repair et New Submission, puis exécutez Microsoft BizTalk Accelerator pour SWIFT Configuration Assistant, le programme de Configuration s’achève avec succès même s’il n’existe aucune base de données A4SWIFT.  
  
 Une base de données A4SWIFT s’affichera dans le **les composants Web pour Message Repair et New Submission** volet de la boîte de dialogue de Configuration d’A4SWIFT, même si cette base de données n’existe pas. Un avertissement est affiché pour le A4SWIFT dans les données de base de données stocke volet, mais qu’avertissement n’empêche pas le processus de configuration à partir de la procédure.  
  
## <a name="upgrade-process-does-not-create-a-new-root-folder"></a>Mise à niveau ne crée pas un dossier racine  
 Le processus de mise à niveau met à jour les fichiers A4SWIFT existants  *\<lecteur\>*: \Program Files\Microsoft BizTalk Accelerator pour dossier A4SWIFT 2.3/3.0. Il ne crée pas un nouveau dossier pour les fichiers mis à niveau, et il modifie le nom du dossier existant à  *\<lecteur\>*: \Program Files\Microsoft BizTalk Accelerator pour SWIFT.  
  
## <a name="canceling-setup-during-an-upgrade-for-a4swift-may-leave-your-system-in-an-unknown-state"></a>Annulation de l’installation pendant une mise à niveau pour A4SWIFT peut laisser votre système dans un état inconnu.  
 Dans certains scénarios, en cliquant sur le **Annuler** bouton pendant une mise à niveau peut laisser les fichiers, les assemblys, les artefacts de BizTalk Server et les clés de Registre intact une fois que le programme d’installation a terminé sa restauration.  
  
 Vous pouvez supprimer manuellement tous les éléments sans aucun problème.  
  
## <a name="download-the-a4swift-setup-exe-file-from-the-web-into-a-temp-folder"></a>Téléchargez le fichier exe du programme d’installation A4SWIFT à partir du Web dans un dossier temporaire  
 Si vous souhaitez installer A4SWIFT à partir d’un fichier exécutable à extraction automatique que vous téléchargez à partir du Web, veillez à télécharger ce fichier dans un dossier temporaire. Ne pas télécharger le fichier dans le dossier racine de BizTalk Server (BizTalk Server de \Program Files\Microsoft \< *votre version*\>).  
  
 Si vous exécutez le fichier exe à partir du dossier racine de BizTalk Server, il s’exécute le serveur BizTalk Server Assistant installation, pas l’Assistant d’installation A4SWIFT.  
  
## <a name="installing-a4swift-in-a-location-other-than-the-default-requires-changes-to-the-bredeploymentexeconfig-file"></a>L’installation d’A4SWIFT dans un emplacement autre que la valeur par défaut nécessite la modification du fichier BREDeployment.exe.config  
 Si vous installez BizTalk Accelerator pour SWIFT dans un chemin d’accès différent du chemin d’accès par défaut de %programfiles%\Microsoft BizTalk Accelerator pour SWIFT, vous devez modifier le fichier BREDeployment.exe.config dans le sous-répertoire SDK\Tools du produit afin de refléter les chemins d’accès corrects pour les BasePoliciesDirectory, SchemasDirectory et VocabularyDirectory.  
  
 Vous devez effectuer cette modification avant de déployer les règles associées avec les schémas SWIFT inclus dans vos projets afin de déployer correctement les règles pertinentes et le vocabulaire.  
  
## <a name="message-repair-is-not-supported-for-certain-batched-message-scenarios"></a>Réparation de message n’est pas prise en charge pour certains scénarios de message par lot  
 A4SWIFT prend en charge la réparation de messages uniquement pour les scénarios de traitement par lot de fragmentation. Dans ces scénarios, seule la partie de l’échange de messages par lot peut être réparée.  
  
## <a name="you-cannot-submit-a-fixed-unparsed-message-from-a-mrsr-site-library-named-anything-other-than-unparsed"></a>Vous ne peuvent pas soumettre un message non analysé fixe d’une bibliothèque de site MRSR autre chose qu’Unparsed nommé  
 Lorsque vous essayez d’envoyer un message non analysé que vous avez résolu à partir d’une bibliothèque de documents MRSR site qui n’est pas nommée « Unparsed », l’opération échoue, car A4SWIFT ne peuvent pas soumettre correctement un message à partir d’une bibliothèque qui n’est pas nommé « Unparsed ».  
  
 Si vous avez une bibliothèque de documents « Non analysé » existante dans le site MRSR avant d’installer la fonctionnalité de rapprochement et le Message Repair, le programme d’installation A4SWIFT crée une bibliothèque pour les messages non analysées intitulée « Non analysé » avec un suffixe.  
  
 Lorsque A4SWIFT reçoit un message qu’il ne peut pas analyser, il achemine le message vers la bibliothèque qui a été créé. Toutefois, lorsque vous essayez d’envoyer un message à partir de cette bibliothèque, l’opération échoue.  
  
 Ce problème est généralement se produire si vous désinstallez A4SWIFT et que vous ne supprimez pas la bibliothèque de documents « Non analysé » à partir du site MRSR.  Lors de la réinstallation SWIFT dans ces circonstances, le programme d’installation crée une nouvelle bibliothèque de documents avec le nom « Unparsed » avec un suffixe. »  
  
 Pour résoudre ce problème, procédez comme suit :  
  
#### <a name="to-name-a-library-unparsed-in-order-to-submit-unparsed-messages"></a>Pour nommer une bibliothèque « Unparsed » afin d’envoyer des messages non analysées  
  
1.  Supprimer la fonctionnalité de Message Repair et rapprochement.  
  
2.  Supprimez manuellement la bibliothèque non analysée. Cela ne sont pas supprimé lors de la désinstallation d’A4SWIFT.  
  
3.  Réinstallez Message Repair et rapprochement. Lors de la réinstallation, la bibliothèque de documents sera créée avec le nom « Unparsed », et vous pouvez envoyer des messages non analysées fixes via cette bibliothèque de documents.  
  
## <a name="bredeployment-utility-cannot-deploy-or-undeploy-policies-if-a4swift-vocabularies-are-not-correctly-configured"></a>Utilitaire de BREDeployment ne peut pas déployer ou annuler le déploiement de stratégies si les vocabulaires A4SWIFT ne sont pas configurés correctement  
 Si vous essayez d’annuler le déploiement de stratégies du moteur de règles d’entreprise A4SWIFT à l’aide de l’outil BREDeployment.exe, et le fichier de configuration BREDeployment.exe ne pointe pas vers l’emplacement de fichier de vocabulaire correct, l’outil peut signaler une erreur. Si vous modifiez l’emplacement dans le fichier de configuration BREDeployment.exe et le nouvel emplacement ne contient-elle pas les fichiers de vocabulaire, vous devez ce problème. L’erreur vous informe que les vocabulaires n’ont pas été trouvés et la configuration arrête les stratégies de déploiement ou annulation du déploiement.  
  
 Pour résoudre ce problème, utilisez la norme **Assistant de déploiement du moteur de règles d’entreprise**. Détails de l’interface utilisateur sont [!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)].
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus](../../adapters-and-accelerators/accelerator-swift/known-issues5.md)
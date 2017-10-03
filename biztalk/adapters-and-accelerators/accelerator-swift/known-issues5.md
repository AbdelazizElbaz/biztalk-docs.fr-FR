---
title: Connu Issues5 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, known issues
- BizTalk Accelerator for SWIFT, known issues
- known issues
ms.assetid: 0f1ec7dd-9e74-479a-bdc8-ab9c4397c992
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3b2b5eadcbdbdc357529f4ad8af47d46840d47e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues"></a>Problèmes connus
Cette section contient des informations utiles qui peuvent vous aider à éviter les erreurs avec [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]. Les problèmes connus sont regroupées dans les domaines suivants :  
  
## <a name="message-repair-and-new-submission"></a>Message Repair et New Submission

#### <a name="printing-of-a-repair-document-is-recorded-in-the-history-log-even-if-canceled"></a>L’impression d’un document de réparation est enregistrée dans le journal d’historique, même si annulé  
 Si vous exécutez la commande d’impression d’un document dans la boîte de réception de réparation, puis annulez l’impression, l’impression est toujours entrée dans le journal d’historique. Cela se produit lorsque vous ouvrez le document à réparer dans son [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] écran et cliquez sur la commande Imprimer dans le menu fichier, puis cliquez sur Annuler dans la boîte de dialogue Imprimer. Vous devez ignorer l’entrée dans le journal d’historique.  
  
#### <a name="a-duplicate-signature-can-cause-an-xlangs-error-message"></a>Une signature en double permettre provoquer un message d’erreur XLANG/s  
 Lorsqu’un vérificateur utilise le même certificat comme un réparateur, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] interrompt le message et indique dans un message d’erreur signatures en double ne sont pas autorisés. Toutefois, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] génère également un autre message d’erreur avec une source d’événement de XLANG/s, qui indique que le service XLANG/s a été suspendu. Vous pouvez ignorer ce message.  
  
#### <a name="message-size-can-affect-repair-performance"></a>Taille du message peut affecter les performances de la réparation  
 Si vous essayez de réparer un fichier XML anormalement élevé, les performances du système peuvent nuire considérablement aux lorsque vous ouvrez le fichier XML dans le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire pour le type de message. La consommation de mémoire peut augmenter la consommation du processeur peut diminuer les et peut échouer avec une erreur indiquant la mémoire insuffisante pour terminer l’opération.  
  
#### <a name="the-last-signature-used-to-sign-a-message-successfully-will-be-authenticated-by-authenticate-signatures"></a>La dernière signature utilisée pour signer un message correctement est authentifiée par authentifier des Signatures  
 En cliquant sur le bouton authentifier des Signatures sur un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire valide la signature pour la phase que vous êtes dans uniquement si vous avez déjà signé le formulaire. Dans le cas contraire, il valide la signature pour l’étape précédente, s’il existe un et enregistre l’erreur suivante :  
  
 L’utilisateur de signature n’est pas configuré correctement pour le rôle < stage_name > service < department_name >.  
  
 Par exemple, supposons que vous êtes dans une phase d’approuver immédiatement après une étape de vérification. Si vous n’êtes pas encore inscrit le formulaire en tant que l’approbateur et que vous cliquez sur authentifier les Signatures, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] authentifie la signature que le vérificateur est utilisé, pas de signature de votre approbateur et enregistre l’erreur précédente.  

#### <a name="a4swift-cleanup-tool-doesnt-delete-templates"></a>Outil de nettoyage A4SWIFT ne supprime pas les modèles  
 L’outil de nettoyage A4SWIFT n’effectue les opérations suivantes :  
  
-   Supprime tous les modèles MT MRSR site  
  
-   Supprime tous les contrats et les profils de partenaires à partir du site MRSR  
  
-   Supprime tous les utilisateurs, rôles et services  
  
-   Annule l’inscription de BizTalk Server A4SWIFT à partir du site MRSR  
  
#### <a name="the-a4swiftmrsrdepartment-property-is-set-to-an-empty-string-for-a-message-that-did-not-parse"></a>La propriété A4SWIFT_MRSRDepartment est définie sur une chaîne vide pour un message qui n’est pas analysée  
 Lors de l’orchestration de réparation de messages achemine vers la MessageBox un message non analysé qui a été résolu, il définit le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_MRSRDepartment propriété vide de chaîne et de le promouvoir. Un port d’envoi ne sera pas en mesure de vous abonner sur cette propriété.  
  
#### <a name="cannot-save-a-department-if-the-sso-service-has-been-stopped"></a>Impossible d’enregistrer un service si le service d’authentification unique a été arrêté.  
 Si vous essayez d’ajouter un service lorsque le service SSO est arrêté, vous recevrez une erreur indiquant que le serveur SSO principal \<machinename > a échoué. Vérifiez que SSO est configuré et que le service SSO est exécuté sur ce serveur.  
  
#### <a name="a-department-name-must-not-contain-the-character-"></a>Nom d’un service ne doit pas contenir le caractère « ~ »  
 Un nom de service qui contient le caractère « ~ » entraîne des problèmes avec la base de données A4SWIFT.  
  
#### <a name="signing-infopath-forms"></a>Signature des formulaires Infopath  
 La signature des formulaires InfoPath doit être effectuée manuellement.  
  
## <a name="security"></a>Sécurité

#### <a name="mixing-trusted-and-untrusted-hosts-can-enable-spoofing"></a>Mélange des hôtes approuvés et non approuvés permettre activer l’usurpation  

 Il est possible d’usurper des messages SWIFT liées à partir d’autres non approuvé [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] héberger des applications. Il s’agit uniquement d’un problème lors de l’exécution en mode de confiance mixte (lorsque les hôtes approuvés et non approuvés exécuter des applications dans le même [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] groupe). Vous pouvez réduire ce risque à l’aide de composants de pipeline de résolution de tiers pour identifier la source du message SWIFT liées. Cela n’est pas nécessaire lors de l’exécution dans un environnement de confiance totale ou pour la majorité des scénarios d’utilisation. Vous devez suivre le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] des recommandations pour la création d’applications sécurisées lorsque vous mélangez approuvés et non fiables hôtes. 
 
## <a name="miscellaneous"></a>Divers

#### <a name="the-cacheentries-setting-may-be-reset-by-a-setup-program-affecting-performance"></a>Le paramètre CacheEntries peut être réinitialisé par un programme d’installation, affectent les performances  
 La clé de Registre CacheEntries détermine le nombre maximal de groupes de règles mis en cache par le service de mise à jour de moteur de règles métier. Le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] programme d’installation affecte par défaut CacheEntries à 32. Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] programme d’installation modifie HKEY_LOCAL_MACHINE\SOFTWARE\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]\BusinessRules\3.0\CacheEntries à 512 pour optimiser les performances. Toutefois, dans certaines circonstances, CacheEntries peut être réinitialisé automatiquement. Cela peut affecter les performances du système.  
  
 Mises à jour du moteur de règles peuvent changer CacheEntries comprise entre 512 et 32. Après avoir installé une mise à jour du moteur de règles, réinitialisez manuellement CacheEntries à 512, si nécessaire.  
  
 Bien que le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] programme d’installation définit CacheEntries de 32 à 512, désinstallation [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] ne réinitialise pas CacheEntries comprise entre 512 et 32.  
  
 Pour plus d’informations, consultez la rubrique « Règle moteur et réglage des paramètres de Configuration » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
#### <a name="building-a-pipeline-project-may-result-in-a-large-number-of-warnings"></a>Génération d’un projet de pipeline peut entraîner un grand nombre d’avertissements  
 Lorsque vous ajoutez l’assembleur SWIFT à un pipeline d’envoi ou le désassembleur SWIFT à un pipeline de réception et puis générez le projet de pipeline contenant ces pipelines, vous pouvez recevoir une série d’avertissements liés aux composants de pipeline. Ces avertissements indiquent que Visual Studio n’a pas trouvé dépendances. Vous pouvez corriger la condition qui est à ces avertissements en modifiant la propriété copie locale de l’assembly SWIFTAsm ou SWIFTDasm dans le dossier de référence, comme suit :  
  
1.  Dans l’Explorateur de solutions de Visual Studio, développez votre projet de pipeline, puis le **références** nœud.  
  
2.  Sous le nœud Références, sélectionnez le **SWIFTAsm** assembly et/ou la **SWIFTDasm** assembly.  
  
3.  Dans le volet Propriétés, modifiez la valeur pour le **copie locale** propriété **False**.  
  
4.  Avec le bouton droit de votre projet de pipeline, puis cliquez sur **Build**.  
  
    > [!NOTE]
    >  Vous ne devez pas voir les avertissements relatifs à des dépendances est introuvable.   
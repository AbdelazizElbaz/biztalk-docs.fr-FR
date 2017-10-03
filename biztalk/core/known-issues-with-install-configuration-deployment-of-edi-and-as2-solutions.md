---
title: "Problèmes connus avec l’Installation, la Configuration et déploiement de Solutions EDI et AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dee03f0-2447-4cc2-90f4-e9b73caa0f39
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 406e69cafd4822a0f8f436b471d53c4e815dce32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-installation-configuration-and-deployment-of-edi-and-as2-solutions"></a>Problèmes connus avec l'installation, la configuration et le déploiement des solutions EDI et AS2
Cette rubrique décrit des problèmes connus liés au déploiement et à la gestion de solutions EDI et AS2 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="blank-strings-were-imported-for-party-properties"></a>Des chaînes vides ont été importées pour des propriétés du tiers  
 **Symptôme**  
  
 Lorsque vous avez importé des liaisons EDI/AS2 à partir d'un fichier de liaison dans une application BizTalk, certaines propriétés sensibles du tiers, telles que des mots de passe ou des informations de sécurité/d'authentification, n'ont pas été importées. Des chaînes vides ont été définies pour ces propriétés.  
  
 **Cause possible**  
  
 BizTalk Server n'importe pas les paramètres de champs sensibles. L'importation de ces paramètres pourrait créer un problème de sécurité.  
  
 **Résolution**  
  
 Vous devez définir manuellement les valeurs des champs EDI sensibles après avoir importé les liaisons sur un autre ordinateur.  
  
## <a name="ftp-adapter-is-not-supported-natively-in-64-bit-mode"></a>L'adaptateur FTP n'est pas pris en charge de manière native en mode 64 bits  
 L'adaptateur FTP ne peut pas s'exécuter en mode 64 bits natif. Si vous utilisez un adaptateur FTP dans votre solution EDI pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez l'exécuter sous WOW64 sur une plateforme Windows 64 bits.  
  
## <a name="some-edias2-artifacts-are-still-active-after-unconfiguring"></a>Certains artefacts d'EDI/AS2 sont toujours actifs après annulation de la configuration  
 Après que vous avez annulé la configuration de la fonction EDI/AS2 Microsoft de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], certains artefacts de BizTalk Server liés au traitement EDI et AS2 restent actifs dans le contexte de la configuration de groupe BizTalk. Ces derniers incluent des pipelines EDI et AS2 ainsi que l'orchestration du traitement par lots. Vous pouvez donc continuer à effectuer un traitement EDI et AS2 de base, même après avoir annulé la configuration de la fonction EDI/AS2 Microsoft. Pour désactiver cette fonctionnalité, vous devez désactiver, arrêter ou supprimer les ports associés au traitement EDI et AS2.  
  
## <a name="you-receive-the-error-failed-to-configure-edias2-status-reporting-functionalities"></a>Le message d'erreur « Échec de la configuration des fonctionnalités de rapport d'état EDI/AS2 » s'affiche  
 **Symptôme**  
  
 Lors de la configuration du rapport d'état d'exécution EDI/AS2, vous obtenez le message d'erreur « Échec de la configuration des fonctionnalités de rapport d'état EDI/AS2 ».  
  
 **Cause possible**  
  
 Ce message d'erreur peut s'afficher si la configuration initiale des Outils BAM a été annulée.  
  
 **Résolution**  
  
 Configurez les Outils BAM avant de configurer les fonctionnalités de rapport d'état EDI ou AS2.  
  
## <a name="recovering-a-deleted-artifact-from-the-biztalk-edi-application-requires-you-to-reconfigure-the-edias2-runtime"></a>La récupération d'un artefact supprimé à partir de l'application EDI BizTalk requiert une reconfiguration du composant d'exécution EDI/AS2  
 Évitez d'utiliser l'application EDI BizTalk pour vos propres artefacts. Cette application contient les artefacts d'EDI/AS2 déployés au cours de la configuration d'EDI/AS2. Il est recommandé de créer une application séparée et d'y ajouter une référence à l'application EDI BizTalk. Toutefois, si vous supprimez un artefact EDI/AS2 d'une application EDI BizTalk, vous pouvez récupérer de cet état en annulant la configuration du composant d'exécution EDI/AS2 de BizTalk de chaque ordinateur d'exécution composant le groupe (ou en annulant la configuration du composant d'exécution EDI/AS2 du groupe, puis en annulant sa configuration sur chaque ordinateur d'exécution accessible). Pour éviter toute perte de données, il est déconseillé de supprimer les bases de données ou les activités BAM d'EDI/AS2. Vous pouvez ensuite reconfigurer le composant d'exécution EDI/AS2 sur tous les ordinateurs d'exécution du groupe pour récupérer les artefacts EDI/AS2 supprimés.  
  
## <a name="numeric-transaction-set-group-control-and-interchange-control-values-may-be-truncated"></a>Les valeurs de document informatisé numérique, de contrôle du groupe et de contrôle de l'échange peuvent être tronquées  
 Les champs de plage de valeurs pour les numéros de contrôle de l'échange, les numéros de référence de document informatisé et les numéros de contrôle du groupe vous permettent d'entrer des valeurs supérieures à la valeur maximale autorisée. Lorsque vous enregistrez la configuration, ces valeurs sont tronquées à la valeur maximale.  
  
 La valeur maximale pour les champs de propriété X12 est 999 999 999.  
  
 La valeur maximale pour les champs de propriété EDIFACT est 99 999 999 999 999.  
  
## <a name="control-numbers-are-reset-to-1-after-upgrade"></a>Les numéros de contrôle sont réinitialisés à 1 suite à une mise à niveau  
 Après la mise à niveau, vous pouvez remarquer que tous les numéros de contrôle affichés dans les propriétés EDI d’un tiers ont été réinitialisés à la valeur minimale par défaut 1 et affichent la valeur maximale par défaut de 999999999 (X12) ou 99999999999999 (EDIFACT). La mise à niveau n'affecte pas les valeurs de préfixe ou de suffixe.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Affiche les valeurs minimales et maximales à utiliser pour le numéro de contrôle. Le numéro de contrôle actuel est conservé pendant la mise à niveau ; Toutefois il n’est pas affiché dans les propriétés EDI du tiers.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des Solutions EDI et AS2](../core/troubleshooting-edi-and-as2-solutions.md)   
 [Vue d’ensemble de l’installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)   
 [Vue d’ensemble de la configuration de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/aa58c43f-8f0e-4a5c-89b9-db7b8a852a72)   
 [Étapes d’optimisation de l’environnement après configuration](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md)
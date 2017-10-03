---
title: Configurer BizTalk Accelerator pour SWIFT | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e34b0b2d-f563-468b-b6b9-536f0df96f52
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eaa9812243ef7d5ff4bb8b902ac7aee48e54ab99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-biztalk-accelerator-for-swift"></a>Configurer BizTalk Accelerator pour SWIFT

Configurer le [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)]. 

Lorsque vous installez [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)], il existe une case à cocher qui vous permet d’exécuter la configuration automatiquement. Ou bien, vous pouvez ouvrir la Configuration BizTalk Accelerator pour SWIFT (A4SWIFT) répertoriée dans vos applications.

Cette rubrique vous montre comment configurer le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] accelerator, comment exporter ou importer une configuration et liste également les étapes à la configuration.

## <a name="configure-a4swift"></a>Configurer A4SWIFT

1. Ouvrez BizTalk Accelerator pour SWIFT (A4SWIFT) Configuration.
2. Sélectionnez **MCRR**. MCRR est disponible uniquement si vous avez installé le **Message Repair et New Submission** composants.
3. Lorsque vous êtes invité **vous souhaitez créer un nouveau groupe de base de données**:

  * Sélectionnez cette option pour créer de nouveaux groupes indiqués dans le **groupe** volet. 
  * Pour joindre un groupe existant de la base de données, désactivez cette option.

3. Si vous avez installé **les composants Web pour Message Repair et New Submission**, puis sélectionnez **WebService**.
4. Sélectionnez le site web pour héberger le service Web d’A4SWIFT. Par défaut, le Site Web par défaut est sélectionné.
5. Sélectionnez **appliquer la Configuration**.
6. Dans **Résumé**, vérifiez les paramètres de configuration, puis cliquez sur **configurer**. 

    > [!TIP] 
    > Vous pouvez enregistrer les paramètres de configuration dans un fichier XML si vous le souhaitez.

7. Sélectionnez **Terminer** lorsque la configuration est terminée.

## <a name="export-or-import-a-configuration"></a>Exporter ou importer une configuration
Vous pouvez exporter les paramètres de configuration d’A4SWIFT dans un fichier XML. Ces paramètres peuvent ensuite être importés pour configurer une autre installation d’A4SWIFT. 

### <a name="export-the-configuration"></a>Exporter la configuration

1. Ouvrez Microsoft BizTalk Accelerator pour SWIFT Configuration, puis sélectionnez **exporter la Configuration**.
2. Dans **enregistrer en tant que**, accédez au dossier où vous souhaitez enregistrer le fichier de configuration, entrez un nom pour le fichier de configuration, puis **enregistrer**.
3. Lorsque vous exportées avec succès, sélectionnez **OK**.

### <a name="import-a-configuration"></a>Importer une configuration
1. Ouvrez Microsoft BizTalk Accelerator pour SWIFT Configuration, puis sélectionnez **importer la Configuration**.
2. Accédez au dossier qui contient le fichier de configuration, sélectionnez le fichier, puis **importation**.

## <a name="post-configuration-steps"></a>Étapes à la configuration

### <a name="add-users-to-the-a4swift-users-group"></a>Ajouter des utilisateurs au groupe utilisateurs d’A4SWIFT

Après avoir configuré le [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)], ajoutez le compte qui exécute l’instance de l’hôte BizTalkServerApplication pour le **A4SWIFT utilisateurs** groupe (*pas* le **A4SWIFT administrateurs** groupe). 

**Étapes**:

1. Ouvrez **Services**. Services est également disponible dans **le Gestionnaire de serveur**, puis **outils**. 
2. Dans la liste, recherchez **groupe BizTalk des services BizTalk : BizTalkServerApplication**. 
3. Sélectionnez en double pour ouvrir ses propriétés.
4. Dans le **session** onglet, notez que le compte d’utilisateur est répertorié comme **ce compte**.
5. Ouvrez **utilisateurs et groupes locaux** (gestion de l’ordinateur), puis recherchez le **A4SWIFT utilisateurs** groupe. Ajoutez le compte d’utilisateur à ce groupe.

> [!TIP] 
> Le compte de l’instance doit cette appartenance de groupe pour le composant d’exécution hôte Message Repair pour accéder à la base de données BizTalk Server.

### <a name="check-the-identity-of-the-application-pool"></a>Vérifier l’identité du pool d’applications
Le service web A4SWIFT_MRSR est hébergé dans une application dans IIS. L’identité du pool d’applications *ne peut pas* agisse Service réseau. Modifier l’identité du pool d’applications à un compte local ou de domaine qui est membre de la **A4SWIFT utilisateurs** groupe.

**Étapes**:

1. Ouvrez **le Gestionnaire des Services Internet**. Le Gestionnaire des services Internet est également disponible dans **le Gestionnaire de serveur**, puis **outils**. 
2. Développez le **Site Web par défaut**, puis sélectionnez le service web A4SWIFT_MRSR. 
3. Sélectionnez **les paramètres de base**. Le nom du pool d’applications est répertorié.
4. Dans le volet gauche, sélectionnez **Pools d’applications**, puis sélectionnez votre pool d’applications.
5. Sélectionnez **paramètres avancés**et modifier le **identité** si nécessaire.
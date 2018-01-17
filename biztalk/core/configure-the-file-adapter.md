---
title: "Configurer l’adaptateur File | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- File adapters, configuring
- configuring [File adapters], about configuring File adapters
- configuring [File adapters]
ms.assetid: 1e0c7e20-80f8-469b-b423-34a2b90f9ec3
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2f2de6a4c4cae93db90f0fb2cfc79321bfc7b3e
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="configure-the-file-adapter"></a>Configurer l’adaptateur de fichier
Comment configurer l’adaptateur de fichier, de lire les recommandations de sécurité et d’afficher les autorisations requises.

Vous pouvez créer un emplacement de réception et à l’aide du port d’envoi [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], ou par programme. Cette rubrique se concentre sur la [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] console. Pour connaître les étapes par programme, accédez à [créer l’emplacement de réception ou port d’envoi par programme](../core/create-the-receive-location-and-send-port-programmatically.md).

> [!IMPORTANT]
> **En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** , vous pouvez vous connecter à un partage de fichiers Azure à l’aide de l’adaptateur File. Le compte de stockage Azure doit être monté sur votre serveur BizTalk Server. [Prise en main avec un stockage de fichier Azure sur Windows](https://docs.microsoft.com/azure/storage/storage-dotnet-how-to-use-files#mount-the-file-share) répertorie les étapes de montage.

## <a name="security-recommendations"></a>Recommandations de sécurité

L'adaptateur FILE permet de transférer des fichiers entre BizTalk Server et un répertoire. Il est vivement recommandé de respecter les informations suivantes pour la sécurisation et le déploiement de l'adaptateur FILE dans votre environnement.  
  
-   N’ouvrez pas de ports pour se connecter à un partage de fichiers dans le réseau de périmètre. Vous devez utiliser l'adaptateur FILE dans des environnements approuvés, tel qu'un intranet. 
  
-   Définir des listes de contrôle d’accès discrétionnaire (DACL) dans la réception des répertoires de dépôt de l’emplacement. Par exemple, vous devez définir des autorisations en lecture, écriture et suppression de fichiers et de sous-dossiers pour le répertoire dans lequel l'emplacement de réception des fichiers sélectionne des messages, afin que seuls les utilisateurs autorisés puissent déposer des messages dans cet emplacement.  
  
-   Lorsque vous utilisez l'adaptateur FILE pour extraire des données critiques, il est recommandé d'utiliser le protocole IPSec (Internet Protocol Security).  
  
## <a name="required-permissions"></a>Autorisations requises

Gestionnaires d’adaptateur exécutent dans le contexte de sécurité de l’instance d’hôte sélectionnée pour le Gestionnaire d’adaptateur. L’instance d’hôte utilise le `Logon` propriété dans le  ***nom d’hôte* -propriétés de l’Instance hôte** dans Administration de BizTalk. Cela `Logon` compte doit disposer des autorisations spécifiques pour tous les dossiers ou partages utilisés par l’adaptateur File.

Le compte d’utilisateur instance hôte utilisé par le gestionnaire requiert les autorisations suivantes. Un ✔ implique l’autorisation est nécessaire. Une entrée vide signifie que l’autorisation n’est pas nécessaire.

| Permissions | Gestionnaire de réception | Gestionnaire d'envoi |
| --- | --- | --- |
| Contrôle total | ✔ <br/> au niveau du partage (si l’accès à un partage de fichiers) |  | 
| Parcours du dossier / exécuter le fichier |  | ✔ <br/> au niveau du fichier | 
| Liste des dossiers / lecture de données | ✔ <br/> au niveau du fichier | ✔ <br/> au niveau du fichier | 
| Attributs de lecture | | ✔ <br/> au niveau du fichier | 
| Lire les attributs étendus | | ✔ <br/> au niveau du fichier | 
| Créer des fichiers / écrire des données | | ✔ <br/> au niveau du fichier | 
| Créer des dossiers / Ajout de données | | ✔ <br/> au niveau du fichier | 
| Suppression des sous-dossiers et fichiers | ✔ <br/> au niveau du fichier | ✔ <br/> au niveau du fichier | 
| Autorisations de lecture | | ✔ <br/> au niveau du fichier | 
| Modifier | | ✔ <br/> au niveau du partage (si l’accès à un partage de fichiers) |

> [!TIP] 
> Au niveau du fichier, ouvrez le **les autorisations avancées** sur le fichier ou dossier pour voir ces autorisations.

> [!NOTE] 
> Chaque hôte ne peut être associé qu'à un seul gestionnaire de réception.  

## <a name="configure-the-receive-location"></a>Configurer l’emplacement de réception
  
> [!NOTE]
>  Avant d’exécuter la procédure suivante, vous devez avoir déjà ajouté un unidirectionnel port de réception. Consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).  
  
1.  Dans la console Administration de BizTalk Server, développez successivement [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], **Groupe BizTalk**, **Applications**, puis l’application sous laquelle créer un emplacement de réception.  
  
2.  Dans le volet gauche, cliquez sur le **Ports de réception** nœud. Dans le volet droit, cliquez avec le bouton droit sur le port de réception associé à un emplacement de réception existant ou auquel associer un nouvel emplacement, puis cliquez sur **Propriétés**.  
  
3.  Dans le volet gauche de la **propriétés du Port de réception** boîte de dialogue, sélectionnez **emplacements de réception**et sur le volet droit, double-cliquez sur un existant emplacement de réception ou cliquez sur **nouveau** pour créer un nouvel emplacement de réception.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section, sélectionnez **fichier** dans la liste déroulante, puis tapez **configurer** pour configurer les propriétés de transport pour l’emplacement de réception.  
  
5.  Dans le **général** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Dossier de réception**|Obligatoire. Entrez le chemin d’accès au dossier sur le système de fichiers, le partage réseau, ou le partage de fichiers Azure où le fichier de gestionnaire de réception lit les fichiers. Vous pouvez entrer le chemin d’accès directement dans le **dossier de réception** texte zone, ou sélectionnez-le dans le système de fichiers à l’aide de la **Parcourir** bouton. Lorsque vous recherchez le dossier, vous pouvez également créer un dossier à l’aide **créer un nouveau dossier**.<br /><br /> Si vous utilisez un partage de stockage de fichiers Azure, entrez `\\yourfilestoragename.file.core.windows.net\yourfilesharename`. <br /><br />**Type :** chaîne <br/><br/>**Remarque :** ne définissez pas le **dossier de réception** propriété vers un dossier qui utilise le système de fichiers distribués NT avec un lien symbolique. Si vous utilisez un système de fichiers distribués NT, vous ne pouvez utiliser les dossiers des chemins d’accès direct au réseau dans l’adaptateur File les emplacements de réception. <br /><br /> Pour connaître les restrictions sur cette propriété, consultez [Restrictions relatives à la configuration de l’adaptateur de fichier](../core/restrictions-when-configuring-the-file-adapter.md). <br/><br/>**Remarque :** l’URI pour un envoi de port ou de réception emplacement ne peut pas dépasser 256 caractères.|  
    |**Masque de fichier**|Obligatoire. Indiquer le masque des fichiers. Ce masque peut contenir la valeur générique standard «\*».<br /><br /> **Valeur par défaut :** \*.xml<br /><br /> **Type :** chaîne<br /><br /> Pour connaître les restrictions sur cette propriété, consultez [Restrictions relatives à la configuration de l’adaptateur de fichier](../core/restrictions-when-configuring-the-file-adapter.md).|  
    |**Adresse publique**|Indiquer l'adresse publique de cet emplacement. BizTalk Server expose cette adresse aux partenaires externes.<br /><br /> Si cette propriété n'est pas spécifiée, le moteur d'exécution la remplace par :<br /><br /> file://\<*dossier de réception*\>/\<*masque de fichier*\><br /><br /> La valeur de cette propriété exige un préfixe d'adaptateur.<br /><br /> **Type :** chaîne<br /><br /> **Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|  
    |**Nombre de tentatives**|Indiquer le nombre de tentatives d'accès à l'emplacement de réception sur le partage réseau en cas d'indisponibilité temporaire.<br /><br /> **Valeur par défaut :** 5<br /><br /> **Type :** Long<br /><br /> **Valeur minimale :** 0<br /><br /> **Valeur maximale :** MAX_LONG|  
    |**Intervalle (min)**|Indiquer l'intervalle (en minutes) devant séparer chaque tentative d'accès à l'emplacement de réception sur le partage réseau en cas d'indisponibilité temporaire.<br /><br /> **Valeur par défaut :** 5 minutes<br /><br /> **Type :** Long<br /><br /> **Valeur minimale :** 0<br /><br /> **Valeur maximale :** MAX_LONG|  
  
6.  Sur le **authentification** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Utilisez ces informations d’identification lors de l’hôte n’a pas accès au partage réseau**| Requis uniquement lorsque vous utilisez un partage réseau ou un partage de fichiers Azure. <br /><br /> **Valeur par défaut :** False<br /><br /> **Type :** booléenne|  
    |**Nom d'utilisateur**|Si vous utilisez un partage réseau, entrez le nom d’utilisateur qui a accès au partage. <br /><br />  Si à l’aide d’un stockage de fichier Azure partage, entrez le nom de votre compte de stockage.<br/><br/>**Type :** chaîne <br /><br />**Remarque :** si plusieurs emplacements de réception mappés au même partage réseau sont configurés avec les autres informations d’identification, puis les mêmes informations d’identification doivent être utilisées pour tous les emplacements de réception. Windows ne permet pas d'établir plusieurs connexions à un partage réseau depuis le même ordinateur si vous tentez d'utiliser plusieurs jeux d'informations d'identification.|  
    |**Mot de passe**|Si vous utilisez un partage réseau, entrez le mot de passe pour le compte qui a accès au partage réseau.<br /><br />  Si à l’aide d’un stockage de fichier Azure partage, entrez la clé d’accès de compte de stockage ; qui est répertorié dans le portail Azure.<br /><br /> **Type :** chaîne|  
  
7.  Dans le **le traitement par lot** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nombre de messages dans un lot**|Indiquez le nombre maximal de messages à soumettre en un lot.<br /><br /> **Valeur par défaut :** 5<br /><br /> **Type :** Int<br /><br /> **Valeur minimale :** 1<br /><br /> **Valeur maximale :** 256|  
    |**Taille de lot maximale (en octets)**|Indiquer le nombre maximal d'octets par lot.<br /><br /> **Valeur par défaut :** 102400<br /><br /> **Type :** Int<br /><br /> **Valeur minimale :** 1024<br /><br /> **Valeur maximale :** MAX_LONG|  
  
     L'adaptateur FILE limite le lot à la première valeur atteinte : nombre maximal de messages ou nombre d'octets maximal autorisé.  
  
9. Sélectionnez **OK**.  
  
10. Entrez les valeurs appropriées dans le **propriétés de l’emplacement de réception** boîte de dialogue pour terminer la configuration de l’emplacement de réception, puis cliquez sur **OK** pour enregistrer les paramètres. Pour plus d’informations sur la **propriétés des emplacements de réception** boîte de dialogue, consultez [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  

## <a name="configure-the-send-port"></a>Configurer le port d’envoi

1.  Dans la console Administration de BizTalk Server, créez un port d’envoi ou double-cliquez sur un port d’envoi existant pour le modifier. Consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Configurez toutes les options de port d’envoi et spécifiez **fichier** pour le **Type** option dans le **Transport** section de la **général** onglet.  
  
2.  Sélectionnez le **configurer** situé en regard **Type**.  
  
3.  Dans le **général** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Emplacement de destination**|Obligatoire. Entrez le chemin d’accès à l’emplacement sur le système de fichiers, partage public ou le partage de fichiers Azure pour écrire les messages de sortie. Vous pouvez entrer le chemin d’accès directement dans le **l’emplacement de Destination**, ou sélectionnez-le dans le système de fichiers à l’aide de la **Parcourir** bouton. Lorsque vous parcourez le dossier dans le **rechercher un dossier** boîte de dialogue, vous pouvez également créer un nouveau dossier en cliquant sur **créer un nouveau dossier**.<br /><br /> Si vous utilisez un partage de stockage de fichiers Azure, entrez `\\yourfilestoragename.file.core.windows.net\yourfilesharename`.<br /><br /> **Type :** chaîne <br /><br />**Remarque :** l’URI pour un envoi de port ou de réception emplacement ne peut pas dépasser 256 caractères.|  
    |**Nom de fichier**|Indique le nom du fichier dans lequel le gestionnaire d'envoi FILE écrit le message.<br /><br /> Pour connaître les restrictions sur cette propriété, y compris l’utilisation des macros dans le nom de fichier, consultez [Restrictions relatives à la configuration de l’adaptateur de fichier](../core/restrictions-when-configuring-the-file-adapter.md).|  
    |**Mode de copie**|Définir le mode de copie à utiliser lors de l’écriture d’un message dans un fichier. Les valeurs valides sont :<br /><br /> **Ajouter.** le gestionnaire d'envoi FILE ouvre un fichier s'il existe et ajoute un message à la fin du fichier. Si le fichier n'existe pas, il le crée.<br /><br /> **Remplacer**. le gestionnaire d'envoi FILE ouvre un fichier s'il existe et remplace son contenu. Si le fichier n'existe pas, il le crée.<br /><br /> **Créer de nouveaux**. si aucun fichier n'existe, le gestionnaire d'envoi FILE en crée un et y enregistre des éléments. si le fichier existe déjà, il signale une erreur et applique la procédure logique commune pour les nouvelles tentatives sur l'adaptateur pour les ports d'envoi. Il s'agit d'un mode de copie par défaut pour le gestionnaire d'envoi FILE.|  
    |**Autoriser le Cache lors de l’écriture**|Précise si la mise en cache du système de fichiers doit être appliquée lors de l'écriture d'un message dans un fichier.<br /><br /> Les options admises sont les suivantes :<br /><br /> **False** n’utilisez pas le cache du système de fichiers.<br /><br /> **True** utiliser le cache du système de fichiers.<br /><br /> **Valeur par défaut :** False **Important :** définissant cette propriété sur **True** peut augmenter les performances de l’adaptateur File au risque de perdre des données lorsqu’il existe une perte d’alimentation et de toutes les données sont écrites sur le disque.|  
    |**Utiliser un fichier temporaire lors de l’écriture**|Définit si le fichier de sortie doit d'abord être écrit dans un fichier temporaire, puis renommé une fois l'opération d'écriture terminée. Si cette option est activée, le fichier temporaire doit être créé avec l’extension **BTS-WIP**.<br /><br /> Les options valides sont<br /><br /> **True** l’adaptateur File crée un fichier temporaire lors de l’écriture dans le dossier cible.<br /><br /> **False** l’adaptateur File ne crée pas un fichier temporaire lors de l’écriture dans le dossier cible.<br /><br /> **Valeur par défaut :** False **Remarque :** cette option est disponible uniquement lorsque le **CopyMode** est définie sur une valeur de **créer un nouveau**|  
  
4.  Sur le **authentification** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Utilisez ces informations d’identification lors de l’hôte n’a pas accès au partage réseau**| Requis uniquement lorsque vous utilisez un partage réseau ou un partage de fichiers Azure. <br /><br /> **Valeur par défaut :** False<br /><br /> **Type :** booléenne|  
    |**Nom d'utilisateur**|Si vous utilisez un partage réseau, entrez le nom d’utilisateur qui a accès au partage. <br /><br />  Si à l’aide d’un stockage de fichier Azure partage, entrez le nom de votre compte de stockage.<br /><br /> **Type :** chaîne|  
    |**Mot de passe**|Si vous utilisez un partage réseau, entrez le mot de passe pour le compte qui a accès au partage réseau.<br /><br />  Si à l’aide d’un stockage de fichier Azure partage, entrez la clé d’accès de compte de stockage ; qui est répertorié dans le portail Azure.<br /><br /> **Type :** chaîne|  
  
5.  Sélectionnez **OK** pour enregistrer vos paramètres.  

## <a name="set-the-properties-for-a-dynamic-send-port"></a>Définir les propriétés d’un port d’envoi dynamique
  
 Un port d'envoi dynamique ne fournit aucune option de configuration relative au transport dans la console Administration de BizTalk, car ces propriétés doivent être fournies avec les propriétés de contexte associées au message. Vous pouvez définir celles-ci dans un pipeline personnalisé ou dans une orchestration. Pour définir les propriétés de configuration de message dans une orchestration, vous pouvez procédez comme suit :  
  
-   Ajouter un **construire un Message** forme à votre orchestration.  
  
-   Configurer le **construire un Message** forme construire un nouveau message. par exemple Message_2.  
  
-   Ajouter un **assignation du Message** à mettre en forme le **construire un Message** forme.  
  
-   Ajoutez le code pour le **assignation du Message** forme pour initialiser le message que vous avez construit et définir les propriétés de configuration approprié pour le message. Le code suivant initialise un message intitulé Message_2 qui a été construit avec un **construire un Message** mettre en forme, puis définit deux propriétés de configuration pour le message. Dans ce scénario, le message Message_1 a été initialement reçu par l'orchestration :  
  
    ```  
    Message_2=Message_1;  
    Message_2(FILE.CopyMode)= 0; //0=Append  
    Message_2(FILE.AllowCacheOnWrite)= true;  
    Message_2(FILE.UseTempFileOnWrite)= true;  
    ```  
 
  
## <a name="configure-the-receive-or-send-handler"></a>Configurer la réception ou le Gestionnaire d’envoi
  
1.  Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **cartes**.  
  
2.  Dans la liste développée des adaptateurs, cliquez sur **fichier**, dans le volet droit, cliquez sur la réception ou envoi gestionnaire que vous souhaitez configurer. Sélectionnez **propriétés**.  
  
3.  Dans le **nom d’hôte** , sélectionnez l’ordinateur hôte pour exécuter le gestionnaire.  
  
4.  Cliquez sur **OK**.  

## <a name="more-topics-in-this-section"></a>Autres rubriques de cette section

[Créer le fichier de l’emplacement de réception ou port d’envoi par programme](../core/create-the-receive-location-and-send-port-programmatically.md)

[Propriétés et schéma de propriété de l’adaptateur de fichier](../core/file-adapter-property-schema-and-properties.md)

[Restrictions relatives à la configuration de l’adaptateur de fichier](../core/restrictions-when-configuring-the-file-adapter.md)

## <a name="see-also"></a>Voir aussi

 [Ports pour les serveurs de l’envoi et la réception](../core/ports-for-the-receive-and-send-servers.md)   
 [Droits d’utilisateur de sécurité minimales](../core/minimum-security-user-rights.md)
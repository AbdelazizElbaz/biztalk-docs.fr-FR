---
title: "Créer par programme le fichier de port d’envoi ou emplacement de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 558a414c-60bc-4f62-9397-a023ed4937fb
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92737ca115e95c5cd66fdf0e03cf05296ef16088
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="programmatically-create-the-file-receive-location-or-send-port"></a>Créer par programme le fichier de l’emplacement de réception ou port d’envoi
Comment créer un fichier de port de réception et le port d’envoi par programme. Pour utiliser le [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], accédez à [configurer l’adaptateur File](../core/configure-the-file-adapter.md).

L'adaptateur FILE stocke ses informations de configuration dans la base de données SSO. Vous pouvez configurer les emplacements de réception et le modèle objet de programmation à l’aide de l’Explorateur BizTalk de ports d’envoi. 
 
## <a name="create-the-receive-location"></a>Pour créer un emplacement de réception

Le modèle d’objet de l’Explorateur BizTalk expose le **IReceiveLocation** interface de configuration qui contient la **TransportTypeData** propriété en lecture/écriture. Cette propriété accepte le jeu de propriétés de configuration de l'emplacement de réception FILE sous la forme d'une chaîne XML composée d'une paire nom/valeur.  
  
Le **TransportTypeData** propriété de la **IReceiveLocation** interface n’a pas à définir. Si elle n'est pas définie, les valeurs par défaut de configuration de l'emplacement de réception FILE sont utilisées.  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir pour l'emplacement de réception FILE.  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|**FileNetFailRetryCount**|Long|Nombre de tentatives d'accès à l'emplacement de réception sur le partage réseau en cas d'indisponibilité temporaire.|Entier<br /><br /> Valeur minimale : 0<br /><br /> Valeur maximale : MAX_LONG|Si cette propriété n'est pas définie, la valeur par défaut est définie sur 5 fois.|  
|**FileNetFailRetryInterval**|Long|Intervalle en minutes devant séparer chaque tentative d'accès à l'emplacement de réception sur le partage réseau en cas d'indisponibilité temporaire.|Entier<br /><br /> MinimumValue : 0<br /><br /> Valeur maximale : MAX_LONG|Si cette propriété n'est pas définie, la valeur par défaut est définie sur 5 minutes.|  
|**BatchSize**|Long|Nombre de fichiers que l'emplacement de réception peut envoyer au serveur en une fois.|Entier<br /><br /> Valeur minimale : 1<br /><br /> Valeur maximale : 256|Si cette propriété n'est pas définie, la valeur par défaut est définie sur 20 fichiers.|  
|**FileMask**|Chaîne|Masque de fichier utilisé par l'emplacement de réception.|Chaîne<br /><br /> La longueur combinée de FilePAth et FileMask est limitée à 256 caractères.|Si cette propriété n'est pas définie, la valeur par défaut est définie sur *.xml.|  
|**Chemin d’accès**|Chaîne|Chemin d'accès du dossier surveillé par l'emplacement de réception.|Chaîne<br /><br /> Requis<br /><br /> La longueur combinée de FilePAth et FileMask est limitée à 256 caractères.|Vous devez spécifier **Important :** le dossier de fichiers créé pour l’emplacement de réception doit avoir l’autorisation d’écriture pour les informations d’identification du Gestionnaire de réception configuré sur l’emplacement de réception.|  
|**Nom d’utilisateur**|Chaîne|Nom d'utilisateur du compte utilisé pour accéder au dossier.|La longueur minimale : 0<br /><br /> Longueur maximale : 256|Si ni le nom d'utilisateur ni le mot de passe ne sont spécifiés, les informations d'identification de l'hôte sont utilisées.<br /><br /> Si la propriété a la valeur Null (vt=”1”), la valeur stockée dans la base de données de configuration est utilisée.|  
|**Mot de passe**|Chaîne|Mot de passe du compte utilisé pour accéder au dossier.|La longueur minimale : 0<br /><br /> Longueur maximale : 256|Si ni le nom d'utilisateur ni le mot de passe ne sont spécifiés, les informations d'identification de l'hôte sont utilisées.<br /><br /> Si la propriété a la valeur Null (vt=”1”), la valeur stockée dans la base de données de configuration est utilisée.|  
  
 Le code suivant illustre le format de la chaîne XML que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps>  
   <FilePath vt="8">C:\Temp</FilePath>  
   <BatchSize vt="19">20</BatchSize>  
   <FileMask vt="8">*.xml</FileMask>  
   <FileNetFailRetryCount vt="19">5</FileNetFailRetryCount>  
   <FileNetFailRetryInterval vt="19">5</FileNetFailRetryInterval>  
   \<Username vt=”8”>MyDomain\MyUsername</Username>  
   \<Password vt=”8”>PASSWORD</Password>  
</CustomProps>  
  
```  

## <a name="create-the-send-port"></a>Pour créer un port d'envoi

Elles sont stockées dans un jeu de propriétés XML personnalisé. Le `bts_file_properties.xsd` schéma de propriété de fichier envoi gestionnaire définit les propriétés spécifiques à l’adaptateur de fichier. Ces propriétés permettent de configurer les ports d'envoi FILE et de transmettre des informations spécifiques à l'adaptateur au sein du serveur.  
  
Le modèle d’objet de l’Explorateur BizTalk expose le **ITransportInfo** interface configuration adaptateur pour les ports d’envoi File, qui contient le **TransportTypeData** propriété en lecture/écriture. Cette propriété accepte le jeu de propriétés de configuration du gestionnaire d'envoi FILE sous la forme d'une chaîne XML composée d'une paire nom/valeur.  
  
 Définition de la **TransportTypeData** propriété de la **ITransportInfo** interface n’est pas requise. Si elle n'est pas définie, les valeurs par défaut de configuration du gestionnaire d'envoi FILE sont utilisées.  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir par programme dans le modèle objet de l'Explorateur BizTalk pour l'emplacement du gestionnaire d'envoi FILE.  
  
|Nom de la propriété|Type| Description|  
|-------------------|----------|-----------------|  
|**CopyMode**|Long|Définir le mode de copie à utiliser lors de l’écriture d’un message dans un fichier. Les valeurs valides sont :<br /><br /> **Ajouter (0).** le gestionnaire d'envoi FILE ouvre un fichier s'il existe et ajoute un message à la fin du fichier. Si le fichier n'existe pas, il le crée.<br /><br /> **Créer (1).** si le fichier n'existe pas, le gestionnaire d'envoi FILE le crée et y enregistre des éléments. si le fichier existe déjà, il signale une erreur et applique la procédure logique commune pour les nouvelles tentatives sur l'adaptateur pour les ports d'envoi. Il s'agit d'un mode de copie par défaut pour le gestionnaire d'envoi FILE.<br /><br /> **Remplacer (2).** le gestionnaire d'envoi FILE ouvre un fichier s'il existe et remplace son contenu. Si le fichier n'existe pas, il le crée.|  
|**AllowCacheOnWrite**|Booléen|Précise si l'adaptateur FILE utilise la mise en cache du système de fichiers lors de l'écriture de messages dans un fichier.<br /><br /> Les valeurs valides sont :<br /><br /> **True (-1)** l’adaptateur File utilise le fichier système mise en cache lors de l’écriture du fichier de sortie.<br /><br /> **False (0)** Gestionnaire d’envoi du fichier n’utilise pas le fichier système mise en cache lors de l’écriture du fichier de sortie.|  
|**Utiliser un fichier temporaire lors de l’écriture**|Booléen|Définit si vous souhaitez écrire le fichier de sortie dans un fichier temporaire tout d’abord, puis renommez le fichier une fois l’opération d’écriture est terminée. Si cette option est activée, le fichier temporaire doit être créé avec l’extension **BTS-WIP**.<br /><br /> Les valeurs valides sont :<br /><br /> **True (-1)** l’adaptateur File crée un fichier temporaire lors de l’écriture dans le dossier cible.<br /><br /> **False (0)** l’adaptateur File ne crée pas un fichier temporaire lors de l’écriture dans le dossier cible. **Remarque :** cette option est disponible uniquement lorsque le **CopyMode** est définie sur une valeur de **créer nouveau (1)**.|  
  
 Si l'une des propriétés de configuration n'a pas de valeur dans le contexte du message, le gestionnaire d'envoi FILE utilise sa valeur par défaut.  
  
 Vous pouvez définir les propriétés de configuration par programme dans un contexte de message. Vous pouvez les définir dans une orchestration ou dans un composant de pipeline personnalisé. Les règles suivantes s'appliquent dans le cadre de l'utilisation de ces propriétés :  
  
-   Si la propriété de configuration est définie dans une orchestration ou un composant de pipeline personnalisé dans un pipeline de réception, alors :  
  
    -   Si un message est envoyé à un port d'envoi statique, la valeur de la propriété est remplacée par la valeur configurée pour ce port d'envoi.  
  
    -   Si un message est envoyé à un port d'envoi dynamique, la valeur de la propriété n'est pas remplacée.  
  
-   Si une propriété de configuration est définie dans un composant de pipeline personnalisé dans un pipeline d'envoi, alors :  
  
    -   La valeur n'est pas remplacée, que le message soit envoyé à un port d'envoi statique ou dynamique.  
  
 Le code suivant illustre le format de la chaîne XML que vous pouvez utiliser pour définir les propriétés :  
  
```  
<CustomProps>  
   <CopyMode vt="19">0</CopyMode>  
   <AllowCacheOnWrite vt="11">-1</AllowCacheOnWrite>  
   <UseTempFileOnWrite vt="11">-1</UseTempFileOnWrite>  
</CustomProps>  
```  



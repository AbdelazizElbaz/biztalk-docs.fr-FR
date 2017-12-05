---
title: "Restrictions relatives à la configuration de l’adaptateur de fichier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [File adapters], restrictions
- File adapters, restrictions
ms.assetid: 8d8137a7-5b16-4ae3-a0a7-6d114324bdf3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6fbf9296e56db816277f9a7a348377bfa4b359d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="restrictions-when-configuring-the-file-adapter"></a>Restrictions relatives à la configuration de l’adaptateur de fichier
Les restrictions et les règles lors de l’utilisation de l’adaptateur file.

## <a name="file-mask-and-file-name-gotchas"></a>Masque de fichier et les problèmes de nom de fichier

Le masque de fichier est une chaîne qui spécifie le type de fichier que le gestionnaire de réception FILE récupère dans l'emplacement de réception. Le nom de fichier est une chaîne qui spécifie le nom du fichier dans lequel le gestionnaire d'envoi FILE écrit le message.  
  
 Les restrictions suivantes s'appliquent aux propriétés Nom de fichier et Masque de fichier :  
  
-   Il n'est possible de spécifier qu'un seul masque de fichier ou nom de fichier par emplacement de réception.  
  
-   Vous ne pouvez pas spécifier le chemin d'accès complet ou une partie du chemin d'accès conjointement avec le masque ou le nom de fichier. Ceux-ci sont toujours constitué d'un nom sans le chemin d'accès.  
  
-   Le masque et le nom de fichier ne respectent pas la casse.  
  
-   Le nom de fichier ne peut contenir aucun des caractères suivants : \< \> : / &#124; " ? * ;  
  
-   Le masque de fichier ne peut contenir aucun des caractères suivants : \< \> : / &#124; " ; 
  
-   Les noms de périphérique réservés suivants ne peut pas être utilisés comme nom d’un fichier : CON, PRN, AUX, CLOCK$, NUL, COM1, COM2, COM3, COM4, COM5, COM6, COM7, COM8, COM9, LPT1, LPT2, LPT3, LPT4, LPT5, LPT6, LPT7, LPT8 et LPT9. En outre, toute combinaison de ces éléments avec des extensions n'est pas autorisée.  
  
-   Les volumes de disque de Windows utilisent la convention de noms par défaut, qui utilise les noms de fichiers longs et courts 8.3 (modèle 8.3). Volumes de disque non désactiver la convention d’affectation de noms de modèle 8.3 et par conséquent utilisent uniquement les noms de fichier longs. 

    Lorsque le modèle 8.3 est activé, les fichiers et les extensions de fichier sont converties par un nom court. Par exemple, `testabcdefgh.docx` est converti en `testab~1.doc`. Notez que le nom de fichier est réduit, et l’extension de fichier est réduite à partir de `.docx` à `doc`.

    Ce comportement a un impact sur la façon dont l’adaptateur File reçoit le fichier. Si un masque de fichier est défini sur `*.xml`, puis les fichiers correspondant à la fois `*.xml` et `*.xmln` extensions sont prélevées. 

    Pour voir si la convention d’affectation de noms de modèle 8.3 est activée sur vos disques, ouvrez une invite de commandes en tant qu’administrateur et tapez `fsutil 8dot3name query c:`, ou `fsutil 8dot3name query d:`, et ainsi de suite. Exemple de sortie se présente comme suit :

    ```
    C:\WINDOWS\system32>fsutil 8dot3name query c:
    The volume state is: 0 (8dot3 name creation is enabled).
    The registry state is: 2 (Per volume setting - the default).
    
    Based on the above two settings, 8dot3 name creation is enabled on c:
    ```
    
    L’adaptateur File utilise la [FindFirstFile fonction](https://msdn.microsoft.com/library/windows/desktop/aa364418(v=vs.85).aspx). Cette fonction comprend les résultats de recherche qui ont les noms de fichiers longs et courts. Pour afficher les noms de fichiers longs et courts dans un dossier, ouvrez une invite de commandes, accédez à votre dossier et tapez `dir /x`. Dans une invite de commandes, vous pouvez également taper `dir c:\foldername /x`.
    
    Si vous modifiez le paramètre 8dot3name sur un volume, nouveaux fichiers utilisent le nouveau paramètre. Tous les fichiers existants conservent leurs noms jusqu'à ce qu’ils sont déplacés. 
    
    Récupère uniquement les fichiers prévues et obtenir de meilleures performances (moins de surcharge) au cours d’une charge plus élevée, il peut être préférable de configurer l’adaptateur File pour utiliser un volume sur lequel 8dot3name est désactivé. 
  
-   La longueur totale du chemin d'accès au fichier, du masque de fichier et du nom de fichier (sans substitution de macro) ne doit pas dépasser 256 caractères. Il s'agit d'une restriction de la base de données MessageBox.  
  
-   Le chemin d'accès au fichier ne peut pas commencer par « `\\`? »  
  
-   Les chemins d'accès ne peuvent pas comporter de lettres correspondant à des lecteurs réseau mappés, car celles-ci sont liées à des sessions utilisateur.  
  
 Le moteur de messagerie BizTalk valide toujours les propriétés Masque de fichier et Nom de fichier au moment de la conception sur la base des éléments répertoriés ci-dessus. L'adaptateur FILE valide également ces propriétés au moment de l'exécution si l'adaptateur envoie le message via un port dynamique.  
  
> [!NOTE]
>  L'adaptateur FILE ne récupère pas les fichiers système ou les fichiers en lecture seule. Seuls les fichiers se trouvant sur le disque sont récupérés, à l'exception des fichiers de périphérique.  

## <a name="using-macros-in-file-names"></a>À l’aide de macros dans les noms de fichiers

Vous pouvez définir un ensemble prédéfini de macros pour créer de façon dynamique les fichiers dans lesquels le gestionnaire d'envoi FILE écrit des messages. Avant de créer un fichier dans le système de fichiers, le gestionnaire d'envoi FILE remplace toutes les macros dans le nom de fichier par leurs valeurs individuelles. Vous pouvez utiliser plusieurs macros dans un nom de fichier.  
  
 Vous pouvez utiliser les macros de nom de fichier lors de la configuration du gestionnaire d'envoi FILE à l'aide du modèle d'objet de l'Explorateur BizTalk.  
  
 Le gestionnaire d'envoi FILE ne remplace pas les macros par une valeur si les conditions suivantes sont remplies :  
  
-   La propriété système correspondante n'est pas définie.  
  
-   La macro est mal orthographiée.  
  
-   La valeur de la macro contient des symboles de nom de fichier non valides.  
  
 Si une de ces conditions est remplie, le gestionnaire d'envoi FILE conserve les macros telles que dans le nom de fichier (par exemple, Myfile_%MessageID%.xml).  
  
 Le tableau suivant indique les macros prises en charge et décrit leur remplacement par le gestionnaire d'envoi FILE.  
  
|Nom de la macro|Valeur de remplacement|  
|----------------|----------------------|  
|%datetime%|Date et heure UTC au format AAAA-MM-JJThhmmss (par exemple, 1997-07-12T103508).|  
|%datetime_bts2000%|Date et heure UTC au format AAAAMMJJhhmmsss, où sss correspond aux secondes et aux millisecondes (par exemple, 199707121035234 signifie 1997/07/12, 10:35:23 et 400 millisecondes).|  
|%datetime.tz%|Heure et date locales ainsi que le fuseau horaire GMT au format AAAA-MM-JJThhmmssTZD (par exemple, 1997-07-12T103508+800).|  
|%DestinationParty%|Nom du tiers de destination. La valeur provient de la propriété de contexte de message **BTS.DestinationParty**.|  
|%DestinationPartyQualifier%|Qualificateur du tiers de destination. La valeur provient de la propriété de contexte de message **BTS.DestinationPartyQualifier**.|  
|%MessageID%|GUID (Globally Unique Identifier) du message dans BizTalk Server. La valeur provient directement à partir de la propriété de contexte de message **BTS. MessageID**.|  
|%SourceFileName%|Nom du fichier à partir duquel l'adaptateur FILE lit le message. Le nom de fichier inclut l’extension et exclut le chemin d’accès de fichier, par exemple, Sample.xml. Lorsque cette propriété, l’adaptateur File extrait le nom de fichier à partir du chemin de fichier absolu stocké dans le **fichier. ReceivedFileName** propriété de contexte. Si la propriété de contexte n’a pas de valeur : par exemple, si un message a été reçu sur un adaptateur autre que l’adaptateur File : la macro n’est pas remplacée et resteront dans le nom du fichier est (par exemple, C:\Drop\\%sourceFileName%). **Remarque :** implémentation correcte de cette macro requiert que le message de sortie est le même message que le message reçu.|  
|%SourceParty%|Nom du tiers source qui a envoyé le message à l'adaptateur FILE. **Remarque :** implémentation correcte de cette macro requiert que le message de sortie est le même message que le message reçu.|  
|%SourcePartyQualifier%|Qualificateur du tiers source qui a envoyé le message à l'adaptateur FILE. **Remarque :** implémentation correcte de cette macro requiert que le message de sortie est le même message que le message reçu.|  
|%time%|Heure UTC au format hhmmss.|  
|%time.tz%|Heure locale ainsi que le fuseau horaire GMT au format hhmmssTZD (par exemple, 124525+530).|  
  
 
## <a name="receive-folder-and-destination-location-properties-gotchas"></a>Recevoir des pièges de propriétés d’emplacement du dossier et de destination

L'emplacement de réception FILE est une chaîne contenant le chemin d'accès à un dossier sur un système de fichiers ou un partage réseau depuis lequel le gestionnaire de réception FILE lit des fichiers. L'emplacement de destination FILE est une chaîne contenant le chemin d'accès à un dossier sur un système de fichiers ou un partage réseau dans lequel le gestionnaire d'envoi FILE écrit des fichiers.  
  
 Les restrictions suivantes s'appliquent aux propriétés Dossier de réception et Emplacement de destination :  
  
-   Existence du chemin de fichier sur un partage réseau ou système de fichiers n’est pas requis sur le temps lorsque vous spécifiez la propriété de l’utilisateur.  
  
-   Le chemin d'accès au fichier doit toujours être absolu.  
  
-   Vous pouvez spécifier le chemin d’accès à l’aide du format de Universal Naming Convention (UNC) (par exemple, \\ \\ < *server* \> \\ <  *partager*\>).  
  
-   Si le chemin d’accès de fichier est au format UNC, le nom du serveur ne doit pas contenir les caractères suivants : ' ~ ! @ # $ ^ & * ( ) = + [ ] { } \ &#124; ; : ' " , \< \> / ? ;  
  
-   Vous ne pouvez pas utiliser de parent (\\... \\) et en cours (\\.\\) des symboles de dossier dans n’importe quelle partie du chemin de fichier.  
  
-   Le chemin d'accès au fichier ne respecte pas la casse.  
  
-   Le chemin d’accès de fichier ne peut contenir aucun des caractères suivants : \< \> : / &#124; " ? * ;  
  
-   Vous ne pouvez pas utiliser les noms de périphérique réservés suivants dans le chemin d'accès au fichier : CON, PRN, AUX, CLOCK$, NUL, COM1, COM2, COM3, COM4, COM5, COM6, COM7, COM8, COM9, LPT1, LPT2, LPT3, LPT4, LPT5, LPT6, LPT7, LPT8 et LPT9.  
  
-   La longueur totale du chemin d'accès au fichier, ou du nom du fichier (sans substitution de macro) ne doit pas dépasser 256 caractères. (La base de données MessageBox impose cette restriction.)  
  
-   L’adaptateur de fichier ne prend pas en charge la spécification Unicode du chemin de fichier (par exemple, «\\\\?\\»).  
  
 Restrictions relatives à la propriété Dossier de réception uniquement :  
  
-   Ne définissez pas la propriété de dossier de réception vers un dossier qui utilise le système de fichiers distribués Microsoft Windows NT avec un lien symbolique. Si vous utilisez un système de fichiers distribués Windows NT, vous ne pouvez utiliser les dossiers des chemins d’accès direct au réseau dans l’adaptateur File les emplacements de réception.  
  
-   Lorsque des documents sont envoyés à un chemin d'accès UNC et que plusieurs serveurs reçoivent les documents à l'emplacement de réception pour l'adaptateur FILE, un seul serveur récupère et traite la plupart des documents envoyés. Pour plus d’informations sur la modification du nom de fichier, consultez la section de l’adaptateur de réception du fichier de [adaptateur File](../core/file-adapter.md).  
  
 Restrictions relatives à la propriété Dossier d'envoi uniquement :  
  
-   Il se peut que l'adaptateur FILE ne dispose pas de ressources de système d'exploitation suffisantes pour traiter simultanément les messages d'un lot lorsqu'il est exécuté sur un système d'exploitation non-serveur, tel que Microsoft Windows Vista.  
  
 Lors de la conception, l'adaptateur FILE valide le chemin d'accès au fichier à l'aide des règles mentionnées précédemment. Il valide également le message au moment de l'exécution si l'adaptateur envoie le message via un port dynamique à l'aide d'un adaptateur FILE.  
  

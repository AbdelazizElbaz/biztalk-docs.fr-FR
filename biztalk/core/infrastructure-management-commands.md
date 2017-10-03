---
title: "Commandes de gestion d’infrastructure | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f1a88c-19fc-4384-b6bb-f95962a32921
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae58ea03f394b0fe8b7223bdd810dbc72ccb2472
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="infrastructure-management-commands"></a>Commandes de gestion d'infrastructure
Les commandes de configuration de l'utilitaire de gestion de l'analyse BAM (BM) vous permettent d'obtenir et de mettre à jour la configuration BAM.  
  
-   Get-config : Obtient le fichier de configuration BAM.  
  
-   configuration de la mise à jour : met à jour la configuration BAM.  
  
-   Get-changes : répertorie les modifications de l’infrastructure BAM.  
  
-   Get-defxml : Obtient un fichier qui contient tous les artefacts dans la base de données d’importation principale BAM.  
  
> [!NOTE]
>  Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre. L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration. Le commutateur peut être utilisé conjointement avec toute commande BAM classique.  
  
> [!NOTE]
>  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="get-config-command"></a>Commande get-config  
 **Utilisation**  
  
 **BM.exe get-config - FileName :\<fichier de sortie > [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Nom de fichier :\<fichier de sortie >|Chemin d'accès et nom de fichier à utiliser pour enregistrer le fichier de configuration.|  
|Serveur :\<server >|Facultatif : Le nom du serveur à partir duquel obtenir la configuration. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données à partir duquel obtenir la configuration. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Récupère le fichier XML de configuration BAM et l'enregistre dans le fichier spécifié. Le **get-config** commande n’écrase pas le fichier existant.  
  
 **Exemples**  
  
```  
bm.exe get-config -FileName:MyConfig.xml  
bm.exe get-config -FileName:BAMConfiguration.xml -Server:OrdersServer  
```  
  
## <a name="update-config-command"></a>Commande update-config  
 **Utilisation**  
  
 **BM.exe update-config - FileName :\<le fichier de configuration >**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Nom de fichier :\<le fichier de configuration >|Chemin d'accès et nom du fichier de configuration à l'aide duquel mettre à jour l'infrastructure BAM.|  
  
 Met à jour la configuration de l'ordinateur local à partir d'un fichier XML de configuration BAM. Vous pouvez ajouter des noms de serveur et de base de données qui n'existent pas encore dans la configuration actuelle. La modification des noms de serveur ou de base de données disposant déjà d'une infrastructure dynamique déployée se soldera par un échec et bm.exe signalera une erreur.  
  
 Si vous modifiez l'emplacement de dépôt du fichier pour les alertes envoyées sous forme de fichier, vous devez redémarrer les services de notification SQL. Si ces services ne sont pas redémarrés, les alertes continueront à être envoyées à l'emplacement d'origine destiné au dépôt du fichier.  
  
 L'emplacement de dépôt du fichier se modifie en changeant la ligne suivante du fichier de configuration BAM.  
  
 \<Nom de la propriété = « FileDropUNC » >\\\\< nom de l’ordinateur\>\alerts\<cette propriété >  
  
 Pour connaître la procédure mettre à jour les références, consultez [sauvegarde et restauration de BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md).  
  
> [!IMPORTANT]
>  Si vous exécutez une commande update-database, avec un fichier de configuration BAM ne contenant pas de section d'alertes, et que vous avez déjà configuré des alertes BAM, bm.exe écrasera la configuration de sorte que les alertes ne fonctionneront plus.  
  
 **Exemples**  
  
```  
bm.exe update-config -FileName:MyConfig.xml  
```  
  
## <a name="get-changes-command"></a>Commande get-changes  
 **Utilisation**  
  
 **BM.exe get-changes [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel réside la base de données d’importation principale BAM. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Si le nom n’est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Obtient une liste de modifications appliquées à la base de données d'importation principale BAM. Vous pouvez utiliser cette commande pour vérifier les modifications de l'infrastructure de l'analyse BAM. La commande renvoie les informations suivantes :  
  
 Le type de commande de la modification et le fichier à partir duquel la modification a été appliquée.  
  
 L'utilisateur ayant appliqué la modification.  
  
 Les activités qui ont été modifiées.  
  
 Les vues qui ont été modifiées.  
  
 **Exemples**  
  
```  
bm.exe get-changes  
```  
  
 Résultat de la commande  
  
 \#1 : déployer c:\bam\ordermanagement.xml  
  
 By domain\user at 12/30/2005 8:17:08 PM (v3.5.1536.0).  
  
 Activités : OrderMgmt  
  
 Vues : SalesManager  
  
## <a name="get-defxml-command"></a>Commande get-defxml  
 **Utilisation**  
  
 **BM.exe get-defxml - FileName :\<fichier de sortie > [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Nom de fichier :\<fichier de sortie >|Chemin d'accès et nom du fichier dans lequel enregistrer les définitions.|  
|Serveur :\<server >|Facultatif : Le nom du serveur à partir duquel obtenir les définitions. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données à partir duquel obtenir les définitions. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Extrait tous les artefacts de la base de données d'importation principale BAM et les enregistre dans un fichier XML. La commande n'écrase pas les fichiers existants.  
  
 **Exemples**  
  
```  
bm.exe get-defxml -FileName:BAMDefinition.xml  
bm.exe get-defxml -FileName:MyDef.xml -Server:MyServer -Database:MyPI  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)
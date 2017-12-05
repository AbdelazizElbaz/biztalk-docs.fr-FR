---
title: "Déploiement des commandes de définition (modèle d’Observation) BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df7914f3-7a92-4ab2-bd0e-94a2eed4825e
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0dba1e1a4f54b3b33ebca8297cfe9beef7c4f868
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="deployment-of-bam-definition-observation-model-commands"></a>Commandes de déploiement de définitions BAM (modèle d'observation)
Les commandes de déploiement de l'utilitaire de gestion de l'analyse BAM vous permettent d'appliquer, de modifier et de supprimer des définitions.  
  
-   déployer-all : déploie une définition BAM.  
  
-   mise à jour-all : met à jour une définition BAM.  
  
-   Remove-all : supprime une définition BAM.  
  
-   mise à jour-livedataworkbook : met à jour les informations de connexion de base de données dans un classeur de données actives.  
  
-   Regenerate-livedataworkbook : régénère le classeur de données actives sur le serveur.  
  
> [!NOTE]
>  Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre. L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration. Le commutateur peut être utilisé conjointement avec toute commande BAM classique.  
  
> [!NOTE]
>  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="deploy-all-command"></a>Commande deploy-all  
 **Utilisation**  
  
 **BM.exe déployer-all - DefinitionFile :\<fichier def\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|DefinitionFile :\<fichier def\>|Chemin d'accès et nom du fichier contenant les définitions à déployer.|  
|Serveur :\<server\>|Facultatif : Le nom du serveur auquel vous souhaitez déployer les définitions. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données\>|Facultatif : Le nom de la base de données auquel vous souhaitez déployer les définitions. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Déploie tous les artefacts du fichier XML de définitions BAM sur le serveur et la base de données spécifiés. Le fichier peut être un fichier texte contenant les instructions XML de définition BAM ou un classeur Excel BAM. Le fichier de définitions doit comporter des nouveaux artefacts exclusivement. Si le fichier contient des artefacts déjà déployés, le déploiement échouera et génèrera une erreur.  
  
 **Considérations relatives au déploiement de définitions BAM**  
  
 Lors du déploiement d'abonnements aux alertes, les ID utilisateur des abonnés doivent être spécifiés selon le format domaine\utilisateur.  
  
 Distributed transaction coordinator (DTC) service doit être en cours d’exécution sur l’ordinateur sur lequel le **déployer-all** commande est émise.  
  
 Dans le cadre du déploiement d'une définition, l'utilitaire de gestion de l'analyse BAM ne prend en charge que 14 niveaux de dimension dans la vue RTA. Le déploiement de niveaux supplémentaires entraîne l'échec du déploiement.  
  
 Si vous définissez plusieurs vues utilisant des paramètres de langue différents et que vous déployez votre solution sur un serveur utilisant une seule langue, les vues ne pourront pas être déployées. Ce scénario n'est pris en charge que s'il n'existe aucune agrégation planifiée nécessitant OLAP dans le cadre de la définition BAM.  
  
 L'utilitaire de gestion de l'analyse BAM vous impose une limite de 49 vues d'activité déployées lorsque les alertes BAM sont activées. Le nombre de vues d'activité est calculé de la manière suivante : somme de 1 à N vue(s) multipliée par le nombre d'activités parentes.  Par exemple, si vous déployez une vue basée sur deux activités, vous obtenez deux vues d'activité.  Si vous déployez deux vues, l'une concernant deux activités et l'autre, une seule activité, vous disposez de 3 vues d'activité.  
  
 L'utilitaire de gestion de l'analyse BAM bloque le déploiement des définitions BAM comprenant plusieurs rapports de tableau croisé dynamique définis sur la même combinaison RTA et nom de cube. Bm.exe met fin au déploiement et génère l'erreur suivante :  
  
 Déploiement de vue... Erreur : Échec du déploiement de l’analyse BAM.  
  
 Seule une vue de tableau croisé dynamique peut être définie sur une valeur RTA et un cube donnés.  
  
 Les noms suivants sont réservés et entraîneront l'échec du déploiement de la définition :  
  
-   RecordID  
  
-   ActivityID  
  
-   EstVisible  
  
-   IsComplete  
  
-   LastModified  
  
> [!NOTE]
>  Si bm.exe rencontre une erreur lors du déploiement, celui-ci est interrompu et les modifications apportées aux vues et activités sont annulées. Les modifications apportées aux cubes OLAP ne sont pas annulées car OLAP ne prend pas en charge le déploiement transactionnel.  
  
> [!NOTE]
>  Les définitions BAM créées sur un ordinateur utilisant des paramètres régionaux particuliers ne peuvent être déployées sur un ordinateur présentant une configuration de paramètres régionaux différente. Par exemple, une définition BAM générée à l'aide d'une version en anglais de Microsoft Excel sur un ordinateur configuré avec un paramètre régional EN ne peut être déployée sur un ordinateur configuré pour le japonais à l'aide du paramètre régional JA.  
  
 **Exemples**  
  
```  
bm.exe deploy-all -DefinitionFile:MyDef.xml  
bm.exe deploy-all -DefinitionFile:MyWorkbook.xls -Server:machine1  
```  
  
## <a name="update-all-command"></a>Commande update-all  
 **Utilisation**  
  
 **BM.exe update-all - DefinitionFile :\<fichier def\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|DefinitionFile :\<fichier def\>|Chemin d'accès et nom du fichier contenant les définitions à partir desquelles effectuer la mise à jour.|  
|Serveur :\<server\>|Facultatif : Le nom du serveur sur lequel déployer les mises à jour de définition. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données\>|Facultatif : Le nom de la base de données auquel vous souhaitez déployer les mises à jour de définition. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Met à jour certains artefacts du fichier XML de définition BAM. Le fichier peut être un fichier texte contenant les instructions XML de définition BAM ou un classeur Excel BAM. La mise à jour ne supprime pas les artefacts non décrits dans le fichier de définitions actuel. Elle peut ajouter de nouveaux points de contrôle aux activités, mais ne peut pas supprimer des points de contrôle sur les activités déployées. La mise à jour ne peut pas non plus renommer les points de contrôle ni modifier leurs propriétés.  
  
 Une fois qu'une activité a été déployée, les actions que vous pouvez effectuer sur celle-ci sont restreintes. Par exemple, vous pouvez supprimer des éléments d'une activité mais dans ce cas, votre administrateur devra annuler le déploiement de tous les ensembles des activités et des vues BAM, puis les redéployer. Ceci peut causer une interruption de l'affichage et une perte de données si l'administrateur n'effectue pas de sauvegarde et de restauration des données.  
  
> [!NOTE]
>  Vous ne pouvez pas recourir à cette commande pour ajouter de nouvelles activités à une vue existante. Pour ajouter une vue à une activité, vous devez créer une nouvelle vue comprenant cette activité. Vous pouvez ensuite annuler le déploiement de l'ancienne vue, mais rappelez-vous que vous perdrez alors votre historique de données OLAP.  
  
 **Exemples**  
  
```  
bm.exe update-all -DefinitionFile:MyDef.xml  
bm.exe update-all -DefinitionFile:MyWorkbook.xls -Server:machine1  
```  
  
## <a name="remove-all-command"></a>Commande remove-all  
 **Utilisation**  
  
 **BM.exe remove-all DefinitionFile :\<fichier def\> [-Server :\<server\> ] [-base de données :\<base de données\> ]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|DefinitionFile :\<fichier def\>|Chemin d'accès et nom du fichier contenant les définitions à supprimer.|  
|Serveur :\<server\>|Facultatif : Le nom du serveur à partir de laquelle les définitions doivent être supprimées. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données\>|Facultatif : Le nom de la base de données à partir de laquelle les définitions doivent être supprimées. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Supprime tous les artefacts spécifiés dans le fichier XML de définition BAM. Le fichier peut être un fichier texte contenant les instructions XML de définition BAM ou un classeur Excel BAM. La définition de chaque artefact doit correspondre exactement à la définition d'origine utilisée pour le déploiement.  
  
 **Exemples**  
  
```  
bm.exe remove-all -DefinitionFile:MyDef.xml  
bm.exe remove-all -DefinitionFile:MyWorkbook.xls -Server:machine1  
```  
  
## <a name="update-livedataworkbook-command"></a>Commande update-livedataworkbook  
 **Utilisation**  
  
 **BM.exe update-livedataworkbook-nom :\<nom de fichier de classeur de données actives\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Nom :\<classeur des données actives\>|Nom du classeur de données actives à mettre à jour.|  
|Serveur :\<server\>|Facultatif : Le nom du serveur sur lequel réside le classeur. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données\>|Facultatif : Le nom de la base de données sur lequel réside le classeur. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Met à jour les informations de connexion à la base de données d'importation principale BAM du classeur de données actives BAM spécifié.  
  
> [!NOTE]
>  Lorsque vous configurez une nouvelle chaîne de connexion, vous devez redémarrer le service TDDS pour vous assurer que ce service reconnaît le changement. Pour plus d’informations sur le service TDDS, consultez [procédures stockées BAM événement Bus Service](../core/bam-event-bus-service-stored-procedures.md).  
  
 **Exemples**  
  
```  
bm.exe update-livedataworkbook -Name:SalesManager_Live.xls  
bm.exe update-livedataworkbook -Name:SalesManager_Live.xls -Server:SalesSrv  
```  
  
## <a name="regenerate-livedataworkbook-command"></a>Commande regenerate-livedataworkbook  
 **Utilisation**  
  
 **BM.exe regenerate-livedataworkbook - WorkbookName :\<nom de fichier de classeur de données actives\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|WorkbookName :\<nom de fichier de classeur de données actives\>|Nom du classeur à mettre à jour.|  
|Serveur :\<server\>|Facultatif : Le nom du serveur sur lequel réside le classeur. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté. Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.|  
|Base de données :\<base de données\>|Facultatif : Le nom de la base de données sur lequel réside le classeur. Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.|  
  
 Génère un classeur BAM de données actives, mais sans le déployer.  
  
 Exemples  
  
```  
bm.exe regenerate-livedataworkbook -WorkbookName:SalesManager_Live.xls  
bm.exe regenerate-livedataworkbook -WorkbookName:SM_Live.xls -Server:S1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion de l’analyse BAM](../core/bam-management-utility.md)
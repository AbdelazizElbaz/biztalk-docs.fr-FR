---
title: "Commandes de gestion de l’intercepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2be6460-1f81-4bc3-a831-34ff24d65d34
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cccf89cb6c3e1f6ed600c28377e5ad124c5498ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interceptor-management-commands"></a>Commandes de gestion des intercepteurs
Pour prendre en charge la nouvelle fonctionnalité d'intercepteur BAM, quatre nouvelles commandes ont été ajoutées à l'utilitaire de gestion de l'analyse BAM.  
  
 Ces commandes prennent en charge le déploiement, l'extraction et la suppression des intercepteurs. L'une d'entre elles permet également d'afficher la liste des intercepteur configurés.  
  
-   intercepteur de déploiement : déploie une configuration d’intercepteur.  
  
-   Get-interceptorlist : Obtient une liste d’activités sur lequel l’interception est déployée.  
  
-   Get-interceptor : Obtient la configuration de l’intercepteur.  
  
-   l’intercepteur de la suppression : supprime une configuration de l’intercepteur.  
  
> [!NOTE]
>  Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre. L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration. Le commutateur peut être utilisé conjointement avec toute commande BAM classique.  
  
> [!NOTE]
>  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="deploy-interceptor-command"></a>Commande deploy-interceptor  
 **Utilisation**  
  
 **BM.exe déployer-intercepteur - FileName :\<le nom du fichier de Configuration XML > [-Force : True] [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Nom de fichier :\<nom de fichier de Configuration XML >|Nom du fichier XML contenant la configuration d'intercepteur.|  
|Force:True|Facultatif : Force le déploiement de la configuration de l’intercepteur lors de la détection des conflits de noms événement source.|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel déployer l’intercepteur. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données d’importation principale BAM sur laquelle vous pouvez configurer l’intercepteur.|  
  
 Cette commande déploie la configuration d'intercepteur sur la base de données et le serveur spécifiés. Pendant le déploiement, l'utilitaire de gestion de l'analyse BAM effectue les validations suivantes :  
  
-   Validation XSD : la configuration de l’intercepteur est validée par rapport au schéma de configuration de l’intercepteur commun.  
  
-   Validation de l'existence de l'activité (déploiement dans la base de données d'importation principale) et de la validité des points de contrôle (existence et type de données correspondant).  
  
 En cas de collision dans le nom de la source d'événements, un message d'avertissement décrivant la collision est envoyé. En cas de collision, le déploiement échouera à moins que le **– Force : True** indicateur du paramètre est utilisé.  
  
> [!NOTE]
>  Le **– Force : True** paramètre supprime potentiellement les configurations d’intercepteur qui font référence à des sources d’événements portant le même nom. Vous devez utiliser le **get-interceptor** commande pour créer une sauvegarde de la configuration d’intercepteur existante avant d’utiliser le **– Force : True** paramètre.  
  
 **Exemples**  
  
```  
bm.exe deploy-interceptor  -FileName:myInceptor.xml  
bm.exe deploy-interceptor  -FileName:myInceptor.xml -Force:True  
```  
  
## <a name="get-interceptorlist-command"></a>Commande get-interceptorlist  
 **Utilisation**  
  
 **BM.exe get-interceptorlist [-Server :\<serveur >] [-base de données :\<base de données >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Serveur :\<server >|Facultatif : Le nom du serveur à partir de laquelle retourner une liste des intercepteurs déployés. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données d’importation principale BAM à partir de laquelle extraire les intercepteurs déployés.|  
  
 Cette commande retourne une liste des activités, et des sources d'événements associés, pour lesquelles l'interception est activée.  
  
 **Exemple**  
  
```  
bm.exe get-interceptorlist   
```  
  
## <a name="get-interceptor-command"></a>Commande get-interceptor  
 **Utilisation**  
  
 **BM.exe get-interceptor [-Server :\<serveur >] [-base de données :\<base de données >] - FileName : \<le nom du fichier de Configuration XML > [-activité : \<nom de l’activité >] [-EventSource : \<événement Nom de la source >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Serveur :\<server >|Facultatif : Le nom du serveur à partir de laquelle extraire l’intercepteur déployé. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données d’importation principale BAM à partir de laquelle extraire l’intercepteur déployé.|  
|Nom de fichier :\<nom de fichier de Configuration XML >|Nom du fichier XML dans lequel écrire la configuration d'intercepteur.|  
|Activité :\<nom de l’activité >|Facultatif : Spécifie l’activité pour laquelle retourner l’intercepteur configuré. Peut être utilisé conjointement avec la **EventSource** paramètre pour spécifier la configuration à retourner.|  
|EventSource :\<nom Source d’événement >|Facultatif : Spécifie la source d’événement pour lequel retourner l’intercepteur configuré. Peut être utilisé conjointement avec la **activité** paramètre pour spécifier la configuration à retourner.|  
  
 Si aucun nom d'activité ou de source d'événements n'est spécifié, la commande retourne un fichier de configuration valide contenant la configuration d'intercepteur pour l'ensemble des activités et sources d'événements.  
  
 Si seul un nom d'activité est spécifié, la commande retourne un fichier de configuration d'intercepteur valide pour l'ensemble des sources d'événements associées à cette activité.  
  
 Si seul un nom de source d'événements est spécifié, la commande retourne un fichier de configuration d'intercepteur valide pour cette source d'événements sur l'ensemble des activités.  
  
 Si un nom d'activité et un nom de source d'événements sont spécifiés, la commande retourne un fichier de configuration d'intercepteur valide pour cette source d'événements associée à cette activité.  
  
 **Exemples**  
  
```  
bm.exe get-interceptor   
bm.exe get-interceptor  -Activity:ShippingPO  
```  
  
## <a name="remove-interceptor-command"></a>Commande remove-interceptor  
 **Utilisation**  
  
 **BM.exe remove-interceptor [-Server :\<serveur >] [-base de données :\<base de données >] [-activité : \<nom de l’activité >] [-EventSource : \<nom Source d’événements >]**  
  
 **Paramètres**  
  
|Paramètre| Description|  
|---------------|-----------------|  
|Serveur :\<server >|Facultatif : Le nom du serveur sur lequel l’intercepteur est configuré. Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.|  
|Base de données :\<base de données >|Facultatif : Le nom de la base de données sur lequel l’intercepteur est configuré.|  
|Activité : \<nom de l’activité >|Facultatif : Spécifie l’activité pour laquelle supprimer l’intercepteur spécifié. Peut être utilisé conjointement avec la **EventSource** paramètre pour spécifier la configuration à retourner.|  
|EventSource : \<nom Source d’événement >|Facultatif : Spécifie la source d’événements pour laquelle supprimer l’intercepteur spécifié. Peut être utilisé conjointement avec la **activité** paramètre pour spécifier la configuration à retourner.|  
  
 Si seul un nom d'activité est spécifié, la commande supprime l'intercepteur pour l'ensemble des sources d'événements associées à cette activité.  
  
 Si seul un nom de source d'événements est spécifié, la commande supprime uniquement cette partie de source d'événements pour l'ensemble des activités.  
  
 **Exemple**  
  
```  
bm.exe remove-interceptor   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)
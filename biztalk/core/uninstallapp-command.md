---
title: Commande UninstallApp | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f45c9530-8138-40f1-b279-1428c5a7fbbc
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea94335882ffbcf01b69c450ef4a5eb80ef4fa3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="uninstallapp-command"></a>Commande UninstallApp
Cette commande permet de désinstaller une application BizTalk de l'ordinateur local et de la supprimer de la liste des programmes dans la fenêtre Ajout/Suppression de programmes du Panneau de configuration. Son action est identique à l'utilisation de l'option Ajout/Suppression de programmes. Si plusieurs fichiers .msi ont été installés pour cette application, tous les éléments installés par ces fichiers .msi sont désinstallés.  
  
 Le nom de l'application que vous spécifiez pour cette commande doit correspondre au nom de l'application tel qu'il est affiché dans la fenêtre Ajout/Suppression de programmes. Si vous ne connaissez pas le nom de l’application, vous pouvez utiliser la **ListPackage** commande pour l’obtenir, comme décrit dans [commande ListPackage](../core/listpackage-command.md).  
  
> [!IMPORTANT]
>  Bien qu'il soit possible de désinstaller une application en double-cliquant sur le fichier .msi, cette opération n'est pas prise en charge. En effet, plusieurs fichiers .msi pouvant être installés pour une même application, cette méthode ne permet pas de désinstaller tous les éléments associés à l'application.  
  
## <a name="usage"></a>Utilisation  
 **« ApplicationName » BTSTask UninstallApp :** *valeur*  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis| Description|  
|---------------|--------------|-----------------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Oui|Nom de l'application BizTalk à désinstaller. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
  
## <a name="sample"></a>Exemple  
 **BTSTask UninstallApp /ApplicationName:MyApplication**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md)   
 [Comment désinstaller une Application BizTalk](../core/how-to-uninstall-a-biztalk-application.md)
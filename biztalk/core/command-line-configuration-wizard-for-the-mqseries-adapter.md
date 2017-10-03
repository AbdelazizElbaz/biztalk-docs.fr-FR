---
title: "Assistant de Configuration de ligne de commande pour l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [MQSeries adapters], silent configuration
- MQSeries adapters, silent configuration
- configuring [MQSeries adapters], Command-Line Configuration Wizard
- Command-Line Configuration Wizard
- MQSeries adapters, Command-Line Configuration Wizard
ms.assetid: cab905d1-fe19-4d6a-be1b-f561e133e1d2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee73b890fca43a3651f22092486e5898862b0b72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="command-line-configuration-wizard-for-the-mqseries-adapter"></a>Assistant de Configuration de ligne de commande pour l’adaptateur MQSeries
L'Assistant inclut quatre options pour les actions d'installation, de désinstallation et de journalisation.  
  
## <a name="syntax"></a>Syntaxe  
 **mqsconfigwiz [/u] [/i config.xml] [/l logfile] [/?]**  
  
|Option| Description|  
|------------|-----------------|  
|**/u**|Désinstalle MQSAgent.|  
|**/i** *config.xml*|Installe MQSAgent à l’aide des informations dans le fichier *config.xml*.|  
|**/l** *logfile*|Enregistre les actions dans le fichier *logfile*.|  
|**/?**|Affiche une boîte de dialogue décrivant les options de ligne de commande.|  
  
 Le contenu du fichier XML incluant les informations de configuration peut varier, selon la version de Windows que vous utilisez. Pour plus d’informations sur le format de fichier de configuration, consultez [le fichier de Configuration XML de l’adaptateur MQSeries](../core/xml-configuration-file-for-the-mqseries-adapter.md).  
  
> [!IMPORTANT]
>  L'adaptateur ne fonctionne pas pendant l'exécution de l'Assistant Configuration.  
  
> [!NOTE]
>  Vous ne pouvez pas reconfigurer MQSAgent à l'aide de l'Assistant Configuration de ligne de commande. Vous devez d’abord exécuter l’Assistant pour désinstaller l’agent (**/u**), puis l’exécuter pour configurer (**/i**).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration silencieuse de l’adaptateur MQSeries](../core/silent-configuration-of-the-mqseries-adapter.md)
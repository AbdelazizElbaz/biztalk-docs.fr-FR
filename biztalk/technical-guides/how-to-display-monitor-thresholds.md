---
title: "Comment afficher des seuils d’analyse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d88b15-0691-49d9-b116-1a2ae95bead9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be3818512f76e95655e0441f039176fe6f855344
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-display-monitor-thresholds"></a><span data-ttu-id="fb4cd-102">Comment afficher des seuils d’analyse</span><span class="sxs-lookup"><span data-stu-id="fb4cd-102">How to Display Monitor Thresholds</span></span>
<span data-ttu-id="fb4cd-103">Pour afficher les seuils d’analyse, utilisez le script décrit dans cette section.</span><span class="sxs-lookup"><span data-stu-id="fb4cd-103">To display monitor thresholds, use the script described in this section.</span></span> <span data-ttu-id="fb4cd-104">Ce script fonctionne pour la plupart des analyses.</span><span class="sxs-lookup"><span data-stu-id="fb4cd-104">This script works for the majority of monitors.</span></span> <span data-ttu-id="fb4cd-105">Il crée un fichier .csv qui contient les colonnes décrites dans le tableau suivant et peut être affiché à l’aide d’Office Excel.</span><span class="sxs-lookup"><span data-stu-id="fb4cd-105">It creates a .csv file that includes the columns described in the following table, and can be viewed using Office Excel.</span></span>  
  
|<span data-ttu-id="fb4cd-106">Colonne</span><span class="sxs-lookup"><span data-stu-id="fb4cd-106">Column</span></span>|<span data-ttu-id="fb4cd-107">Description</span><span class="sxs-lookup"><span data-stu-id="fb4cd-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="fb4cd-108">Type</span><span class="sxs-lookup"><span data-stu-id="fb4cd-108">Type</span></span>|<span data-ttu-id="fb4cd-109">Le type d’objets de que l’analyseur est destiné.</span><span class="sxs-lookup"><span data-stu-id="fb4cd-109">The type of objects the monitor is targeted.</span></span>|  
|<span data-ttu-id="fb4cd-110">DisplayName</span><span class="sxs-lookup"><span data-stu-id="fb4cd-110">DisplayName</span></span>|<span data-ttu-id="fb4cd-111">Le nom complet de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="fb4cd-111">The display name of the monitor.</span></span>|  
|<span data-ttu-id="fb4cd-112">Seuil</span><span class="sxs-lookup"><span data-stu-id="fb4cd-112">Threshold</span></span>|<span data-ttu-id="fb4cd-113">Le seuil utilisé par l’analyse.</span><span class="sxs-lookup"><span data-stu-id="fb4cd-113">The threshold used by the monitor.</span></span>|  
|<span data-ttu-id="fb4cd-114">Alerte sur état</span><span class="sxs-lookup"><span data-stu-id="fb4cd-114">AlertOnState</span></span>|<span data-ttu-id="fb4cd-115">Détermine si l’analyse génère une alerte lorsque l’état change.</span><span class="sxs-lookup"><span data-stu-id="fb4cd-115">Determines whether the monitor generates an alert when the state changes.</span></span>|  
|<span data-ttu-id="fb4cd-116">AutoResolveAlert</span><span class="sxs-lookup"><span data-stu-id="fb4cd-116">AutoResolveAlert</span></span>|<span data-ttu-id="fb4cd-117">Détermine si l’alerte générée sera automatiquement résolue lorsque l’état d’analyseur reviendra au vert.</span><span class="sxs-lookup"><span data-stu-id="fb4cd-117">Determines whether the generated alert will be automatically resolved when the monitor state goes back to green.</span></span>|  
|<span data-ttu-id="fb4cd-118">AlertSeverity</span><span class="sxs-lookup"><span data-stu-id="fb4cd-118">AlertSeverity</span></span>|<span data-ttu-id="fb4cd-119">La gravité de l’alerte générée.</span><span class="sxs-lookup"><span data-stu-id="fb4cd-119">The severity of the generated alert.</span></span>|  
  
#### <a name="to-display-monitor-thresholds"></a><span data-ttu-id="fb4cd-120">Pour afficher des seuils d’analyse</span><span class="sxs-lookup"><span data-stu-id="fb4cd-120">To display monitor thresholds</span></span>  
 <span data-ttu-id="fb4cd-121">Exécutez le script suivant pour créer le fichier .csv qui affiche les seuils d’analyse :</span><span class="sxs-lookup"><span data-stu-id="fb4cd-121">Run the following script to create the .csv file that displays the monitor thresholds:</span></span>  
  
```  
function GetThreshold ([String] $configuration)   
{   
  $config = [xml] ("<config>" + $configuration + "</config>")   
  $threshold = $config.Config.Threshold   
  if($threshold -eq $null)   
  {   
    $threshold = $config.Config.MemoryThreshold   
  }   
  if($threshold -eq $null)   
  {   
    $threshold = $config.Config.CPUPercentageThreshold   
  }   
  if($threshold -eq $null)   
  {   
    if($config.Config.Threshold1 -ne $null -and $config.Config.Threshold2 -ne $null)   
    {   
      $threshold = "first threshold is: " + $config.Config.Threshold1 + " second threshold is: " + $config.Config.Threshold2   
    }   
  }   
  if($threshold -eq $null)   
  {   
    if($config.Config.ThresholdWarnSec -ne $null -and $config.Config.ThresholdErrorSec -ne $null)   
    {   
      $threshold = "warning threshold is: " + $config.Config.ThresholdWarnSec + " error threshold is: " + $config.Config.ThresholdErrorSec   
    }   
  }   
  if($threshold -eq $null)   
  {   
    if($config.Config.LearningAndBaseliningSettings -ne $null)   
    {   
      $threshold = "no threshold (baseline monitor)"   
    }   
  }   
  return $threshold   
}   
#$perfMonitors = get-monitor -Criteria:"IsUnitMonitor=1 and Category='PerformanceHealth'"   
$perfMonitors = Get-ScommanagementPack -DisplayName "BizTalk Server Monitoring" | get-scommonitor | where-object{$_.XmlTag -eq "UnitMonitor" -and $_.Category -eq "PerformanceHealth"}  
  
$perfMonitors | select-object @{name="Target";expression={foreach-object {(Get-SCOMClass -Id:$_.Target.Id).DisplayName}}},DisplayName, @{name="Threshold";expression={foreach-object {GetThreshold $_.Configuration}}}, @{name="AlertOnState";expression={foreach-object {$_.AlertSettings.AlertOnState}}}, @{name="AutoResolveAlert";expression={foreach-object {$_.AlertSettings.AutoResolve}}}, @{name="AlertSeverity";expression={foreach-object {$_.AlertSettings.AlertSeverity}}} | sort Target, DisplayName | export-csv "c:\monitor_thresholds.csv"  
  
```
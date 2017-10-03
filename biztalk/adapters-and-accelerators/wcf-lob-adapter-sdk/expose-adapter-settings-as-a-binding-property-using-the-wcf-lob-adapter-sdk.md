---
title: "Exposer les paramètres de la carte en tant qu’une propriété de liaison à l’aide de WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59728113-917e-4bca-8e1a-609cd6558944
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c72ba43378829c71bfb3379bb70ea274de652c9b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="expose-adapter-settings-as-a-binding-property-using-the-wcf-lob-adapter-sdk"></a>Exposer les paramètres de la carte en tant qu’une propriété de liaison à l’aide de WCF LOB Adapter SDK
Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] utilise les propriétés définies dans différentes classes pour la configuration du pool de connexions, le cache de métadonnées et autres comportements de l’adaptateur. Cette rubrique décrit comment vous pouvez surface ces propriétés en tant que propriétés de liaison, afin que le consommateur de l’adaptateur de les définir via un fichier de configuration.  
  
### <a name="to-surface-an-adapter-setting-as-an-adapter-binding-property"></a>À la surface d’un paramètre de carte comme une propriété de liaison de carte  
  
1.  Démarrez Visual Studio, puis, dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
2.  Choisissez le **l’adaptateur WCF LOB** modèle, puis fournissez les autres informations de projet d’adaptateur.  
  
3.  Parcourir le [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]. Lorsque vous accédez à la **propriétés de la carte** , ajoutez les propriétés de liaison que vous voulez exposer en fournissant un **nom de la propriété**, **type de données**, et  **Valeur par défaut**, puis cliquez sur **ajouter** pour ajouter la nouvelle propriété de l’adaptateur.  
  
4.  Terminer la [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]. Votre projet doit contenir les nouveaux fichiers fournis par l’Assistant.  
  
5.  Dans Visual Studio, dans l’Explorateur de solutions, ouvrez la classe dérivée de l’adaptateur. Par exemple, si le nom de votre projet d’adaptateur est « SampleAdapter », la classe d’adaptateur dérivée sont accessibles dans « SampleAdapter.cs ».  
  
6.  Supprimez les variables privées pour les propriétés que vous souhaitez obtenir et définir les paramètres de la carte. Les variables privées ont été générées par le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)].  
  
7.  Mettre à jour les méthodes get/set pour les valeurs de/à des paramètres de la carte de lecture/écriture. L’exemple suivant utilise une propriété de l’adaptateur pour permettre l’activation des compteurs de performance.  
  
    ```  
    [System.Configuration.ConfigurationProperty("enablePerfCounters", DefaultValue = false)]  
    public bool EnablePerfCounters  
    {  
        get { return environmentSettings.PerformanceCounters.Enabled;    }  
        set { environmentSettings.PerformanceCounters.Enabled = value; }  
    }  
    ```  
  
8.  Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 1 : Développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) [activités de développement](../../esb-toolkit/development-activities.md)
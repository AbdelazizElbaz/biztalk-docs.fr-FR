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
# <a name="expose-adapter-settings-as-a-binding-property-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="ea324-102">Exposer les paramètres de la carte en tant qu’une propriété de liaison à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="ea324-102">Expose adapter settings as a binding property using the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="ea324-103">Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] utilise les propriétés définies dans différentes classes pour la configuration du pool de connexions, le cache de métadonnées et autres comportements de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ea324-103">The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] uses the properties defined in different classes for configuring the connection pool, metadata cache, and other adapter behaviors.</span></span> <span data-ttu-id="ea324-104">Cette rubrique décrit comment vous pouvez surface ces propriétés en tant que propriétés de liaison, afin que le consommateur de l’adaptateur de les définir via un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="ea324-104">This topic describes how you can surface these properties as binding properties, so that the adapter consumer can set them through a configuration file.</span></span>  
  
### <a name="to-surface-an-adapter-setting-as-an-adapter-binding-property"></a><span data-ttu-id="ea324-105">À la surface d’un paramètre de carte comme une propriété de liaison de carte</span><span class="sxs-lookup"><span data-stu-id="ea324-105">To surface an adapter setting as an adapter binding property</span></span>  
  
1.  <span data-ttu-id="ea324-106">Démarrez Visual Studio, puis, dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="ea324-106">Start Visual Studio, and then on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="ea324-107">Choisissez le **l’adaptateur WCF LOB** modèle, puis fournissez les autres informations de projet d’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ea324-107">Choose the **WCF LOB Adapter** template, and then provide the other adapter project information.</span></span>  
  
3.  <span data-ttu-id="ea324-108">Parcourir le [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea324-108">Step through the [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)].</span></span> <span data-ttu-id="ea324-109">Lorsque vous accédez à la **propriétés de la carte** , ajoutez les propriétés de liaison que vous voulez exposer en fournissant un **nom de la propriété**, **type de données**, et  **Valeur par défaut**, puis cliquez sur **ajouter** pour ajouter la nouvelle propriété de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ea324-109">When you get to the **Adapter Properties** page, add the binding properties that you want to expose by providing a **Property name**, **Data type**, and **Default value**, and then click **Add** to add the new adapter property.</span></span>  
  
4.  <span data-ttu-id="ea324-110">Terminer la [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea324-110">Complete the [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)].</span></span> <span data-ttu-id="ea324-111">Votre projet doit contenir les nouveaux fichiers fournis par l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="ea324-111">Your project should contain new files provided by the wizard.</span></span>  
  
5.  <span data-ttu-id="ea324-112">Dans Visual Studio, dans l’Explorateur de solutions, ouvrez la classe dérivée de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ea324-112">In Visual Studio, in Solution Explorer, open the adapter-derived class.</span></span> <span data-ttu-id="ea324-113">Par exemple, si le nom de votre projet d’adaptateur est « SampleAdapter », la classe d’adaptateur dérivée sont accessibles dans « SampleAdapter.cs ».</span><span class="sxs-lookup"><span data-stu-id="ea324-113">For example, if the name of your adapter project is "SampleAdapter", the adapter derived class can be found in "SampleAdapter.cs".</span></span>  
  
6.  <span data-ttu-id="ea324-114">Supprimez les variables privées pour les propriétés que vous souhaitez obtenir et définir les paramètres de la carte.</span><span class="sxs-lookup"><span data-stu-id="ea324-114">Remove the private variables for the properties that you want to get and set from adapter settings.</span></span> <span data-ttu-id="ea324-115">Les variables privées ont été générées par le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea324-115">The private variables were generated by the [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)].</span></span>  
  
7.  <span data-ttu-id="ea324-116">Mettre à jour les méthodes get/set pour les valeurs de/à des paramètres de la carte de lecture/écriture.</span><span class="sxs-lookup"><span data-stu-id="ea324-116">Update the get/set methods to read/write values from/to adapter settings.</span></span> <span data-ttu-id="ea324-117">L’exemple suivant utilise une propriété de l’adaptateur pour permettre l’activation des compteurs de performance.</span><span class="sxs-lookup"><span data-stu-id="ea324-117">The following example uses an adapter property to allow enablement of performance counters.</span></span>  
  
    ```  
    [System.Configuration.ConfigurationProperty("enablePerfCounters", DefaultValue = false)]  
    public bool EnablePerfCounters  
    {  
        get { return environmentSettings.PerformanceCounters.Enabled;    }  
        set { environmentSettings.PerformanceCounters.Enabled = value; }  
    }  
    ```  
  
8.  <span data-ttu-id="ea324-118">Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="ea324-118">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea324-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea324-119">See Also</span></span>  
 <span data-ttu-id="ea324-120">[Didacticiel 1 : Développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) [activités de développement](../../esb-toolkit/development-activities.md)</span><span class="sxs-lookup"><span data-stu-id="ea324-120">[Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) [Development Activities](../../esb-toolkit/development-activities.md)</span></span>
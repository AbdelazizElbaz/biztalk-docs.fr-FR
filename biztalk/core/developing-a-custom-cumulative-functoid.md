---
title: "Développement d’un fonctoid cumulé personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ea2c5fa-ed50-4b76-aee9-0d4adf9e6d8c
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f69ae870269948358f117b07f37d481faced160
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-custom-cumulative-functoid"></a>Développement d'un fonctoid cumulé personnalisé
Utilisez un fonctoid cumulé personnalisé afin d'effectuer des opérations de cumul pour les valeurs qui apparaissent plusieurs fois dans un message d'instance.  
  
 Lorsque vous développez un fonctoid cumulé, vous devez implémenter trois fonctions. Ces fonctions correspondent aux actions d'initialisation, de cumul et d'obtention dont le mappage a besoin pour effectuer le cumul. Avant d'aborder ces fonctions, il est important de traiter le thème de la sécurité des threads.  
  
## <a name="writing-a-thread-safe-functoid"></a>Écriture d'un fonctoid thread-safe  
 Le code du fonctoid doit être thread-safe car, dans les situations de stress, plusieurs instances d'un mappage sont susceptibles d'être exécutées simultanément. Voici quelques-uns des points à ne pas oublier :  
  
-   L'état statique doit être thread-safe.  
  
-   L'état d'instance ne doit pas toujours être thread-safe.  
  
-   Votre conception doit tenir compte d'une exécution dans des conditions de stress élevé. Évitez les verrous dans la mesure du possible.  
  
-   Évitez la nécessité de synchronisation si possible.  
  
 BizTalk Server fournit un mécanisme simple pour réduire la complexité de l'écriture d'un fonctoid cumulé thread-safe. Les trois fonctions ont le même premier paramètre, à savoir une valeur d'index entière. BizTalk Server affecte un numéro unique à la valeur d'index lorsqu'il appelle votre fonction d'initialisation. Vous pouvez utiliser cette valeur comme index dans un tableau contenant des valeurs s'accumulant, comme illustré dans le code suivant :  
  
```  
private HashTable cumulativeArray = new HashTable();  
…  
// Initialization function  
public string InitCumulativeMultiply(int index)  
{  
    cumulativeArray[index] = 1.0;  
    return string.Empty;  
}  
```  
  
 Cet exemple utilise un HashTable au lieu d'un ArrayList. Cela est dû au fait que la fonction d'initialisation est susceptible de ne pas être appelée avec des valeurs d'index chronologiques.  
  
## <a name="implementing-the-three-cumulative-functions"></a>Implémentation des trois fonctions cumulées  
 Vous devrez implémenter trois fonctions pour chaque fonctoid cumulé personnalisé que vous développez. Les fonctions et les méthodes que vous devez appeler dans le constructeur pour les définir sont résumées dans le tableau suivant. Toutes les fonctions retournent des valeurs de chaîne.  
  
> [!NOTE]
>  Vous déterminez le meilleur nom pour chaque fonction, mais chaque fonction doit avoir le nombre et le type d'arguments spécifiés.  
  
|Objectif de la fonction|Arguments|Pour définir une référence|Pour définir le script en ligne|  
|----------------------|---------------|------------------------|--------------------------|  
|Initialisation|**index de type int**|**SetExternalFunctionName**|**SetScriptBuffer** avec `functionNumber` = 0|  
|Cumul|**int index, val, l’étendue de la chaîne de la chaîne**|**SetExternalFunctionName2**|**SetScriptBuffer** avec `functionNumber` = 1|  
|Obtenir|**index de type int**|**SetExternalFunctionName3**|**SetScriptBuffer** avec `functionNumber` = 2|  
  
### <a name="initialization"></a>Initialisation  
 L'initialisation vous permet de préparer les mécanismes que vous utiliserez pour procéder au cumul. Selon vos besoins, vous pouvez initialiser un tableau, réinitialiser une ou plusieurs valeurs ou charger d'autres ressources. La valeur de retour de chaîne n'est pas utilisée.  
  
### <a name="cumulation"></a>Cumul  
 C'est là que vous effectuez l'opération de cumul appropriée à votre fonctoid. BizTalk Server transmet les trois paramètres suivants :  
  
-   **Index.** valeur entière représentant une instance de mappage. Il peut y avoir plusieurs instances de mappage exécutées simultanément.  
  
-   **Val.** chaîne contenant la valeur qui doit être cumulée. À moins que vous n'écriviez un fonctoid cumulé de chaîne, il s'agit d'une valeur numérique.  
  
-   **Étendue.** : chaîne contenant un nombre indiquant quelle valeur d'élément ou d'attribut doit être cumulée. Les valeurs réelles sont déterminées par une implémentation.  
  
 Vous décidez des valeurs à cumuler et des valeurs à ignorer. Vous pouvez par exemple ignorer les valeurs qui ne sont pas inférieures à 0 et lever une exception lorsqu'une valeur n'est pas numérique. **BaseFunctoid** fournit deux fonctions :**IsDate** et **IsNumeric**, pour faciliter la validation.  
  
> [!NOTE]
>  Si vous utilisez **IsDate** ou **IsNumeric** dans un script inline, veillez à définir **RequiredGlobalHelperFunctions** afin que les fonctions sont rendues disponibles pour votre script.  
  
 La valeur de retour de chaîne n'est pas utilisée.  
  
### <a name="get"></a>Obtenir  
 Lorsque BizTalk Server termine son itération parmi toutes les valeurs déterminées par les paramètres de fonctoid dans le mappage, il demande la valeur cumulée. La fonction d'obtention comprend un argument, `Index`, qui est une valeur entière représentant une instance de mappage. Votre fonction doit utiliser la valeur d'index pour rechercher et renvoyer la valeur cumulée sous la forme d'une chaîne.  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous illustre comment créer un fonctoid personnalisé pour effectuer la multiplication cumulée. Il repose sur un fichier de ressources contenant trois ressources de chaîne et une ressource bitmap 16 x 16 pixels.  
  
```  
using System;  
using Microsoft.BizTalk.BaseFunctoids;  
using System.Reflection;  
using System.Text;  
using System.Collections;  
using System.Globalization;  
  
namespace Microsoft.Samples.BizTalk.CustomFunctoid  
{  
    public class CumulativeMultiplyFunctoid : BaseFunctoid  
    {  
        private ArrayList myCumulativeArray = new ArrayList();  
  
        public CumulativeMultiplyFunctoid() : base()  
        {  
            //ID for this functoid  
            ID = 6001;  
  
            // Resource assembly must be ProjectName.ResourceName if building with VS.Net  
            SetupResourceAssembly("Microsoft.Samples.BizTalk.CustomFunctoid.CustomFunctoidResources", Assembly.GetExecutingAssembly());  
  
            // Pass the resource ID names for functoid name, tooltip  
            // description and the 16x16 bitmap for the Map palette  
            SetName("IDS_CUMULATIVEMULTIPLYFUNCTOID_NAME");  
            SetTooltip("IDS_CUMULATIVEMULTIPLYFUNCTOID_TOOLTIP");  
            SetDescription("IDS_CUMULATIVEMULTIPLYFUNCTOID_DESCRIPTION");  
            SetBitmap("IDB_CUMULATIVEMULTIPLYFUNCTOID_BITMAP");  
  
            // Put this string handling function under the Cumulative  
            // Functoid tab in the Visual Studio toolbox for functoids  
            Category = FunctoidCategory.Cumulative;  
  
            // 2 required parameters, no optional parameters  
            SetMinParams(1);  
            SetMaxParams(2);  
  
            // Functoid accepts three inputs  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
            AddInputConnectionType((~ConnectionType.FunctoidCount) & (~ConnectionType.FunctoidIndex) & (~ConnectionType.FunctoidIteration) & (~ConnectionType.FunctoidCumulative) & (~ConnectionType.FunctoidLooping) & (~ConnectionType.Record));  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
  
            // Set the output connection type  
            OutputConnectionType = ConnectionType.AllExceptRecord;  
  
            // Set the Initialize, Cumulative and Get functions  
            SetExternalFunctionName(GetType().Assembly.FullName, "Microsoft.Samples.BizTalk.CustomFunctoid.CumulativeMultiplyFunctoid", "InitCumulativeMultiply");  
            SetExternalFunctionName2("AddToCumulativeMultiply");  
            SetExternalFunctionName3("GetCumulativeMultiply");  
        }  
  
        // Initialization function  
        public string InitCumulativeMultiply(int index)  
        {  
            if (index >= 0)  
            {  
                if (index >= myCumulativeArray.Count)  
                {  
                    myCumulativeArray.Add(1.0);  
                }  
                else  
                {  
                    myCumulativeArray[index] = 1.0;  
                }  
            }  
  
            return "";  
        }  
  
        // Cumulative function  
        public string AddToCumulativeMultiply(int index, string val, string reserved)  
        {  
            if (index < 0 || index >= myCumulativeArray.Count)  
            {  
                return "";  
            }  
  
            if (IsNumeric(val))  
            {  
                double dval = Convert.ToDouble(val, CultureInfo.InvariantCulture);  
                myCumulativeArray[index] = (double)(myCumulativeArray[index]) * dval;  
            }  
            return myCumulativeArray[index].ToString();  
        }  
  
        // Get Function  
        public string GetCumulativeMultiply(int index)  
        {  
            if (index < 0 || index >= myCumulativeArray.Count)  
            {  
                return "";  
            }  
  
            return myCumulativeArray[index].ToString();  
        }  
    }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de BaseFunctoid](../core/using-basefunctoid.md)   
 [Développement d’un fonctoid Inline personnalisé](../core/developing-a-custom-inline-functoid.md)   
 [Fonctoid personnalisé (exemple BizTalk Server)](../core/custom-functoid-biztalk-server-sample.md)
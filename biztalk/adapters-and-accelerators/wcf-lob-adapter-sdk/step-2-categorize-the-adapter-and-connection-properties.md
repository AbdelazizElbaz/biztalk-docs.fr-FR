---
title: "Étape 2 : Classer l’adaptateur et les propriétés de connexion | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45b3dc64-2078-4008-878b-501f727f4a11
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e9d49323695b1070a8065cf7a5e548e61fc5db9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-categorize-the-adapter-and-connection-properties"></a>Étape 2 : Classer l’adaptateur et les propriétés de connexion
![Étape 2 sur 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-2of9.gif "Step_2of9")  
  
 **Durée :** 30 minutes  
  
 Dans cette étape, vous mettez à jour le **EchoAdapterBindingElement** et **EchoAdapterBindingElementExtensionElement** classes pour assigner une catégorie de propriétés de votre adaptateur et de la connexion. En procédant ainsi, les propriétés sont regroupées logiquement par catégorie dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] outils. Par exemple, si vous souhaitez que le **Application**, **EnableAuthentication**, et **nom d’hôte** propriétés apparaissent sous la **connexion** catégorie, comme illustré ci-dessous, vous devez affecter la catégorie de connexion pour chacune des propriétés de l’Application, EnableAuthentication et nom d’hôte.  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/c7c0c013-6651-4c32-9f8b-b546a68a0267.gif "c7c0c013-6651-4c32-9f8b-b546a68a0267")  
  
 De même, si vous souhaitez que le **InboundFileFilter** et **InboundFleSystemWatcherFolder** propriétés apparaissent sous la **entrant** catégorie, comme illustré ci-dessous, vous devez affecter la catégorie entrante à chacun. Si vous souhaitez **nombre** et **EnableConnectionPooling** sous le **divers** catégorie, vous devez affecter la catégorie divers à chacun.  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/2acb7677-8b50-4e45-96a3-42d0e2011f19.gif "2acb7677-8b50-4e45-96a3-42d0e2011f19")  
  
 Gardez à l’esprit que vous pouvez affecter une propriété avec n’importe quel nom de catégorie que vous choisissez. Dans cet exemple, étant donné que la propriété EnableConnnectionPooling n’appartient pas à toutes les autres catégories, nous considérer comme divers (divers). À la propriété InboundFileFilter, car il est utilisé lors du traitement entrant dans l’exemple, il est plus approprié d’affecter entrant à la propriété, plutôt que de divers. Voici la catégorisation complète de la propriété personnalisée pour l’adaptateur de l’écho.  
  
|**Propriété**|**Catégorie**|  
|------------------|------------------|  
|InboundFileFilter|Trafic entrant|  
|InboundFileSystemWatcherFolder|Trafic entrant|  
|Compter|Divers|  
|EnableConnectionPooling|Divers|  
|Application|Connexion|  
|EnableAuthentication|Connexion|  
|HostName|Connexion|  
|EchoInUpperCase|Format|  
  
 En plus de ces modifications, vous modifiez également la méthode Dispose du **EchoAdapterHandlerBase**.  
  
 Pour les propriétés de l’adaptateur exposées par l’adaptateur echo, consultez la section Propriétés de l’adaptateur de le [didacticiel 1 : développer l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant de commencer cette étape, vous devez effectuer [étape 1 : utiliser l’Assistant de développement d’adaptateur LOB WCF pour créer le projet d’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-wcf-lob-adapter-development-wizard-to-create-the-echo-adapter.md). Vous devez également être familiarisé avec les `System.ServiceModel.Configuration.BindingElementExtensionElement` et `System.ServiceModel.Configuration.StandardBindingElement` classes.  
  
## <a name="update-the-echoadapterhandlerbase-dispose-method"></a>Mise à jour de la méthode Dispose de EchoAdapterHandlerBase  
  
1.  Dans **l’Explorateur de solutions**, double-cliquez sur le **EchoAdapterHandlerBase.cs** fichier.  
  
2.  Supprimez l’instruction suivante à partir de la **Dispose** méthode :  
  
    ```csharp  
    throw new NotImplementedException("The method or operation is not implemented.");  
    ```  
  
     La méthode modifiée doit ressembler à ce qui suit :  
  
    ```csharp  
    protected virtual void Dispose(bool disposing)  
    {  
       //  
       //TODO: Implement Dispose. Override this method in respective Handler classes  
       //  
    }  
    ```  
  
## <a name="update-the-adapter-properties-class"></a>Mise à jour de la classe d’adaptateur de propriétés  
  
1.  Dans **l’Explorateur de solutions**, double-cliquez sur le **EchoAdapterBindingElement.cs** fichier.  
  
2.  Dans l’éditeur Visual Studio, développez le **des propriétés personnalisées générées** région.  
  
3.  Pour affecter le **divers** catégorie à la **nombre** propriété, ajoutez l’instruction suivante au début de la **nombre** implémentation.  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    ```  
  
     Le **nombre** implémentation doit correspondre désormais les éléments suivants :  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    [System.Configuration.ConfigurationProperty("count", DefaultValue = 5)]  
    public int Count  
    {  
        get  
        {  
            return ((int)(base["Count"]));  
        }  
        set  
        {  
            base["Count"] = value;  
        }  
    }  
    ```  
  
4.  Pour affecter le **divers** catégorie à la **EnableConnectionPooling** propriété, ajoutez l’instruction suivante au début de la **EnableConnectionPooling** mise en œuvre.  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    ```  
  
5.  Pour affecter le **entrant** catégorie à la **InboundFileFilter** propriété, ajoutez l’instruction suivante au début de la **InboundFileFilter** mise en œuvre.  
  
    ```csharp  
    [System.ComponentModel.Category("Inbound")]  
    ```  
  
6.  Pour affecter le **entrant** categoryto **inboundFleSystemWatcherFolder** propriété, ajoutez l’instruction suivante au début de la **inboundFleSystemWatcherFolder**mise en œuvre.  
  
    ```csharp  
    [System.ComponentModel.Category("Inbound")]  
    ```  
  
7.  Vérification pour vous assurer que le code dans le **des propriétés personnalisées générées** région correspond à ce qui suit :  
  
    ```csharp  
    [System.ComponentModel.Category("")]  
    [System.Configuration.ConfigurationProperty("count", DefaultValue = 5)]  
    public int Count  
    {  
        get  
        {  
            return ((int)(base["Count"]));  
        }  
        set  
        {  
            base["Count"] = value;  
        }  
    }  
  
    [System.ComponentModel.Category("")]  
    [System.Configuration.ConfigurationProperty("enableConnectionPooling", DefaultValue = true)]  
    public bool EnableConnectionPooling  
    {  
        get  
        {  
            return ((bool)(base["EnableConnectionPooling"]));  
        }  
        set  
        {  
            base["EnableConnectionPooling"] = value;  
        }  
    }  
  
    [System.ComponentModel.Category("Inbound")]  
    [System.Configuration.ConfigurationProperty("inboundFileFilter", DefaultValue = "*.txt")]  
    public string InboundFileFilter  
    {  
        get  
        {  
            return ((string)(base["InboundFileFilter"]));  
        }  
        set  
        {  
            base["InboundFileFilter"] = value;  
        }  
    }  
  
    [System.ComponentModel.Category("Inbound")]  
    [System.Configuration.ConfigurationProperty("inboundFileSystemWatcherFolder", DefaultValue = "{InboundFileSystemWatcherFolder}")]  
    public string InboundFileSystemWatcherFolder  
    {  
        get  
        {  
            return ((string)(base["InboundFileSystemWatcherFolder"]));  
        }  
        set  
        {  
            base["InboundFileSystemWatcherFolder"] = value;  
        }  
    }  
  
    #endregion Custom Generated Properties  
    ```  
  
## <a name="update-the-connection-properties"></a>Mettre à jour les propriétés de connexion  
  
1.  Dans **l’Explorateur de solutions**, double-cliquez sur le **EchoAdapterConnectionUri.cs** fichier.  
  
2.  Dans l’éditeur Visual Studio, développez le **des propriétés personnalisées générées** région.  
  
3.  Pour affecter le **Format** catégorie à la **EchoInUpperCase** propriété, ajoutez l’instruction suivante au début de la **EchoInUpperCase** mise en œuvre.  
  
    ```csharp  
    [System.ComponentModel.Category("Format")]  
    ```  
  
4.  Pour affecter le **connexion** catégorie à la **nom d’hôte** propriété, ajoutez l’instruction suivante au début de la **nom d’hôte** implémentation.  
  
    ```csharp  
    [System.ComponentModel.Category("Connection")]  
    ```  
  
5.  Pour affecter le **connexion** catégorie à la **Application** propriété, ajoutez l’instruction suivante au début de la **Application** implémentation.  
  
    ```csharp  
    [System.ComponentModel.Category("Connection")]  
    ```  
  
6.  Pour affecter le **connexion** categoryto **EnableAuthentication** propriété, ajoutez l’instruction suivante au début de la **EnableAuthentication** mise en œuvre.  
  
    ```csharp  
    [System.ComponentModel.Category("Connection")]  
    ```  
  
7.  Vérification pour vous assurer que le code dans le **des propriétés personnalisées générées** région correspond à ce qui suit :  
  
    ```csharp  
    #region Custom Generated Properties  
            [System.ComponentModel.Category("Format")]  
            public bool EchoInUpperCase  
            {  
                get  
                {  
                    return this.echoInUpperCase;  
                }  
                set  
                {  
                    this.echoInUpperCase = value;  
                }  
            }  
  
            [System.ComponentModel.Category("Connection")]  
            public string Hostname  
            {  
                get  
                {  
                    return this.hostname;  
                }  
                set  
                {  
                    this.hostname = value;  
                }  
            }  
  
            [System.ComponentModel.Category("Connection")]  
            public string Application  
            {  
                get  
                {  
                    return this.application;  
                }  
                set  
                {  
                    this.application = value;  
                }  
            }  
  
            [System.ComponentModel.Category("Connection")]  
            public bool EnableAuthentication  
            {  
                get  
                {  
                    return this.enableAuthentication;  
                }  
                set  
                {  
                    this.enableAuthentication = value;  
                }  
            }  
            #endregion Custom Generated Properties  
    ```  
  
8.  Dans Visual Studio, à partir de la **fichier** menu, cliquez sur **Enregistrer tout**.  
  
> [!NOTE]
>  Vous avez enregistré votre travail. Vous pouvez en toute sécurité fermer Visual Studio pour l’instant ou accédez à l’étape suivante, [étape 3 : implémenter la connexion de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md).  
  
## <a name="what-did-i-just-do"></a>Quoi simplement ?  
 Vous mis à jour les classes pour attribuer une catégorie à chaque propriété de l’adaptateur et la connexion exposée par l’adaptateur de l’écho.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous implémentez la connexion, la navigation des métadonnées, recherche et résolution des fonctionnalités et l’échange de messages sortants. Enfin, vous générez et déployez l’adaptateur de l’écho.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Implémenter la connexion de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-implement-the-connection-for-the-echo-adapter.md)   
 [Didacticiel 1 : Développer l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)
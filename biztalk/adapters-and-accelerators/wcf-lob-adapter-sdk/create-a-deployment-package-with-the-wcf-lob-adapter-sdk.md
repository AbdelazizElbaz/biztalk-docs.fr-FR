---
title: "Créer un package de déploiement avec WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10022981-7944-45d6-a78a-4d680a79b010
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed471aa5395b9cc743825807e63e23e5433e6d07
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-deployment-package-with-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="aa4f8-102">Créer un package de déploiement avec WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="aa4f8-102">Create a deployment package with the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="aa4f8-103">Au cours du cycle de développement, vous pouvez générer, déboguer et exécuter votre adaptateur au sein de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aa4f8-103">During the development cycle, you can build, debug, and run your adapter within Visual Studio.</span></span> <span data-ttu-id="aa4f8-104">La sortie d’une solution d’adaptateur est un assembly de la DLL.</span><span class="sxs-lookup"><span data-stu-id="aa4f8-104">The output of an adapter solution is a DLL assembly.</span></span> <span data-ttu-id="aa4f8-105">Vous pouvez créer votre solution d’adaptateur à l’aide de Visual Studio IDE ou utiliser les scripts de devenv.exe pour créer un assembly d’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="aa4f8-105">You can build your adapter solution using Visual Studio IDE or use the devenv.exe scripts to create an adapter assembly.</span></span> <span data-ttu-id="aa4f8-106">Une fois que l’adaptateur est développé et il est prêt pour une utilisation dans un environnement du consommateur de la carte, vous devez créer un package de déploiement qui permet à l’adaptateur doit être installé dans les environnements de test et de production.</span><span class="sxs-lookup"><span data-stu-id="aa4f8-106">Once the adapter is developed and it is ready for use within the adapter consumer's environment, you must create a deployment package that allows the adapter to be installed in test and production environments.</span></span>  
  
 <span data-ttu-id="aa4f8-107">Vous pouvez inclure un projet d’installation de Visual Studio et le déploiement au sein de la solution.</span><span class="sxs-lookup"><span data-stu-id="aa4f8-107">You can include a Visual Studio Setup and Deployment project within the solution.</span></span> <span data-ttu-id="aa4f8-108">Cela peut servir à générer automatiquement un fichier .msi dans le cadre de la build de solution.</span><span class="sxs-lookup"><span data-stu-id="aa4f8-108">This can be used to automatically generate an .msi file as part of the solution build.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa4f8-109">Vous pouvez empêcher le projet d’installation et de déploiement de la génération de chaque fois que vous générez la solution sur votre station de travail en l’excluant via le Gestionnaire de Configuration (dans le menu Build) dans Visual Studio .NET.</span><span class="sxs-lookup"><span data-stu-id="aa4f8-109">You can prevent the Setup and Deployment project from building each time you build the solution on your local workstation by excluding it through the Configuration Manager (on the Build menu) within Visual Studio .NET.</span></span> <span data-ttu-id="aa4f8-110">Si vous excluez un projet à partir d’une build de solution à l’aide de cette méthode, vous n’affectez pas le fichier de solution contrôlée source.</span><span class="sxs-lookup"><span data-stu-id="aa4f8-110">If you exclude a project from a solution build using this method, you do not affect the source controlled solution file.</span></span> <span data-ttu-id="aa4f8-111">Les modifications apportées sont conservées dans le fichier d’options utilisateur solution, qui est spécifique et pas sous contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="aa4f8-111">Changes are maintained within the solution user option file, which is developer-specific and not under source control.</span></span>  
  
 <span data-ttu-id="aa4f8-112">Chaque fois que les nouveaux projets sont ajoutés à votre solution, vous devez penser à mettre à jour et configurer le projet de déploiement pour vous assurer que la sortie du nouveau projet est incluse dans le fichier .msi et que les étapes d’installation de projet spécifiques sont effectuées.</span><span class="sxs-lookup"><span data-stu-id="aa4f8-112">Whenever new projects are added to your solution you must remember to update and configure the deployment project to ensure that the output of the new project is included within the .msi file and that any project-specific installation steps are performed.</span></span>  
  
 <span data-ttu-id="aa4f8-113">Il n’est pas suffisant pour cela, installez simplement la sortie du projet adaptateur sur l’ordinateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="aa4f8-113">It is not enough to just install the output of the adapter project on the user's computer.</span></span> <span data-ttu-id="aa4f8-114">L’adaptateur doit être installé dans global assembly cache (GAC) et le fichier machine.config doit être mis à jour pour inscrire l’adaptateur avec [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aa4f8-114">The adapter needs to be installed in global assembly cache (GAC) and the machine.config file needs to be updated to register the adapter with [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].</span></span>  
  
 <span data-ttu-id="aa4f8-115">Voici une action personnalisée d’exemple qui peut être utilisée pour inscrire ou désinscrire une carte avec [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aa4f8-115">Following is a sample custom action that can be used to register or unregister an adapter with [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)].</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Configuration.Install;  
  
using System.Reflection;  
using System.ServiceModel.Configuration;  
using System.Diagnostics;  
using System.Configuration;  
  
namespace Microsoft.Adapters.Samples.EchoV2  
{  
    //Custom action to register the adapter with WCF configuration in machine.config   
  
    //\<system.serviceModel>  
    //  <extensions>  
    //    <bindingElementExtensions>  
    //      <add name="{BINDINGELEM_NAME}" type="{BINDINGELEM_TYPE}, {Assembly Information}" />  
    //    </bindingElementExtensions>  
    //    <bindingExtensions>  
    //      <add name="{BINDING_NAME}" type="{BINDING_TYPE}, {Assembly Information}" />  
    //    </bindingExtensions>  
    //  </extensions>  
    //  <client>  
    //    <endpoint binding="{BINDING_NAME}" contract="IMetadataExchange" name="{BINDING_SCHEME}" />  
    //  </client>  
    //\</system.serviceModel>  
  
    [RunInstaller(true)]  
    public partial class WCFLOBAdapterInstaller : Installer  
    {  
        private Assembly adapterAssembly;  
        private Type bindingSectionType;  
        private Type bindingElementExtensionType;  
        const string INSTALLER_PARM_INSTALLDIR = "INSTALLDIR";  
        const string BINDING_ASSEMBLY_NAME = "Microsoft.Adapters.Samples.EchoV2.EchoAdapter.dll";  
        const string BINDINGELEM_NAME = "echoAdapterV2";  
        const string BINDINGELEM_TYPE = "Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingElementExtensionElement";  
        const string BINDING_NAME = "echoAdapterBindingV2";  
        const string BINDING_TYPE = "Microsoft.Adapters.Samples.EchoV2.EchoAdapterBindingCollectionElement";  
        const string BINDING_SCHEME = "echov2";  
  
        /// <summary>  
        /// Constructor - initialize the components and register the event handlers  
        /// </summary>  
        public WCFLOBAdapterInstaller()  
        {  
            InitializeComponent();  
            this.AfterInstall += new InstallEventHandler(AfterInstallEventHandler);  
            this.BeforeUninstall += new InstallEventHandler(BeforeUninstallEventHandler);  
        }  
  
        /// <summary>  
        /// Add the WCF configuration information in machine.config when installing the adapter.  
        /// </summary>  
        /// <param name="sender"></param>  
        /// <param name="e"></param>  
        private void AfterInstallEventHandler(object sender, InstallEventArgs e)  
        {  
            try  
            {  
                Debug.Assert(this.Context != null, "Context of this installation is null.");  
                string path = this.Context.Parameters[INSTALLER_PARM_INSTALLDIR] + BINDING_ASSEMBLY_NAME;  
                adapterAssembly = Assembly.LoadFrom(path);  
                Debug.Assert(adapterAssembly != null, "Adapter assembly is null.");  
                bindingSectionType = adapterAssembly.GetType(BINDING_TYPE, true);  
                Debug.Assert(bindingSectionType != null, "Binding type is null.");  
                bindingElementExtensionType = adapterAssembly.GetType(BINDINGELEM_TYPE, true);  
                Debug.Assert(bindingElementExtensionType != null, "Binding element extension type is null.");  
                AddMachineConfigurationInfo();  
            }  
            catch (Exception ex)  
            {  
                throw new InstallException("Error while adding adapter configuration information. " + ex.InnerException.Message);  
            }  
        }  
  
        /// <summary>  
        /// Registers the adapter with the WCF configuration  
        /// NOTE: The   
        /// </summary>  
        public void AddMachineConfigurationInfo()  
        {  
            System.Configuration.Configuration config = ConfigurationManager.OpenMachineConfiguration();  
            Debug.Assert(config != null, "Machine.Config returned null");  
            // add <client><endpoint>               
            ServiceModelSectionGroup sectionGroup = config.GetSectionGroup("system.serviceModel") as ServiceModelSectionGroup;  
            if (sectionGroup != null)  
            {  
  
                bool channelEndpointElementExists = false;  
                // this call can throw an exception if there is problem   
                // loading endpoint configurations - e.g. each endpoint  
                // tries to load binding which in turn loads the DLL  
                ClientSection clientSection = sectionGroup.Client;  
                foreach (ChannelEndpointElement elem in clientSection.Endpoints)  
                {  
                    if (elem.Binding.Equals(BINDING_NAME, StringComparison.OrdinalIgnoreCase) && elem.Name.Equals(BINDING_SCHEME, StringComparison.OrdinalIgnoreCase) && elem.Contract.Equals("IMetadataExchange", StringComparison.OrdinalIgnoreCase))  
                    {  
                        channelEndpointElementExists = true;  
                        break;  
                    }  
                }  
                if (!channelEndpointElementExists)  
                {  
                    Debug.WriteLine("Adding ChannelEndpointElement for : " + BINDING_NAME);  
                    ChannelEndpointElement elem = new ChannelEndpointElement();  
                    elem.Binding = BINDING_NAME;  
                    elem.Name = BINDING_SCHEME;  
                    elem.Contract = "IMetadataExchange";  
                    sectionGroup.Client.Endpoints.Add(elem);  
                    Debug.WriteLine("Added ChannelEndpointElement for : " + BINDING_NAME);  
                }  
  
                // add <bindingElementExtension>  
                if (!sectionGroup.Extensions.BindingElementExtensions.ContainsKey(BINDINGELEM_NAME))  
                {  
                    ExtensionElement ext = new ExtensionElement(BINDINGELEM_NAME, bindingElementExtensionType.FullName + "," + bindingElementExtensionType.Assembly.FullName);  
                    sectionGroup.Extensions.BindingElementExtensions.Add(ext);  
                }  
  
                // add <bindingExtension>  
                if (!sectionGroup.Extensions.BindingExtensions.ContainsKey(BINDING_NAME))  
                {  
                    ExtensionElement ext = new ExtensionElement(BINDING_NAME, bindingSectionType.FullName + "," + bindingSectionType.Assembly.FullName);  
                    sectionGroup.Extensions.BindingExtensions.Add(ext);  
                }  
  
                config.Save();  
            }  
            else throw new InstallException("Machine.Config doesn't contain system.serviceModel node");  
        }  
  
        /// <summary>  
        /// Remove the machine configuration information when uninstalling the adapter  
        /// </summary>  
        /// <param name="sender"></param>  
        /// <param name="e"></param>  
        private void BeforeUninstallEventHandler(object sender, InstallEventArgs e)  
        {  
            try  
            {  
                RemoveMachineConfigurationInfo();  
            }  
            catch (Exception ex)  
            {  
                throw new InstallException("Error while removing adapter configuration information" + ex.InnerException.Message);  
            }  
        }  
  
        /// <summary>  
        /// Unregisters the adapter with WCF configuration  
        /// </summary>  
        public void RemoveMachineConfigurationInfo()  
        {  
            System.Configuration.Configuration config = ConfigurationManager.OpenMachineConfiguration();  
            Debug.Assert(config != null, "Machine.Config returned null");  
            ServiceModelSectionGroup sectionGroup = config.GetSectionGroup("system.serviceModel") as ServiceModelSectionGroup;  
            ChannelEndpointElement elemToRemove = null;  
            if (sectionGroup != null)  
            {  
                // Remove <client><endpoint>  
                foreach (ChannelEndpointElement elem in sectionGroup.Client.Endpoints)  
                {  
                    if (elem.Binding.Equals(BINDING_NAME, StringComparison.OrdinalIgnoreCase) && elem.Name.Equals(BINDING_SCHEME, StringComparison.OrdinalIgnoreCase) && elem.Contract.Equals("IMetadataExchange", StringComparison.OrdinalIgnoreCase))  
                    {  
                        elemToRemove = elem;  
                        break;  
                    }  
                }  
                if (elemToRemove != null)  
                {  
                    Debug.WriteLine("Removing ChannelEndpointElement for : " + BINDING_NAME);  
                    sectionGroup.Client.Endpoints.Remove(elemToRemove);  
                    Debug.WriteLine("Removed ChannelEndpointElement for : " + BINDING_NAME);  
                }  
                // Remove <bindingExtension> for this adapter  
                if (sectionGroup.Extensions.BindingExtensions.ContainsKey(BINDING_NAME))  
                {  
                    sectionGroup.Extensions.BindingExtensions.RemoveAt(BINDING_NAME);  
                }  
                // Remove <bindingElementExtension> for this adapter  
                if (sectionGroup.Extensions.BindingElementExtensions.ContainsKey(BINDINGELEM_NAME))  
                {  
                    sectionGroup.Extensions.BindingElementExtensions.RemoveAt(BINDINGELEM_NAME);  
                }  
                config.Save();  
            }  
            else  
            {  
                throw new InstallException("Machine.Config doesn't contain system.serviceModel node");  
            }  
        }  
  
        /// <summary>  
        /// Use this for testing outside of the Setup project  
        /// </summary>  
        /// <param name="assemblyDirectory">Directory where the adapter assembly is located</param>  
        public static void TestAddConfiguration(string assemblyDirectory)  
        {  
            WCFLOBAdapterInstaller action = new WCFLOBAdapterInstaller();  
            InstallContext context = new InstallContext();  
            // In the Setup project, this is set by selecting custom action  
            // and in Properties setting /INSTALLDIR="[TARGETDIR]\" for CustomActionData  
            context.Parameters.Add("INSTALLDIR", assemblyDirectory);  
            action.Context = context;  
            action.AfterInstallEventHandler(null, null);  
        }  
  
        /// <summary>  
        /// Use this for testing outside of the Setup project  
        /// </summary>  
        /// <param name="assemblyDirectory">Directory where the adapter assembly is located</param>  
        public static void TestRemoveConfiguration(string assemblyDirectory)  
        {  
            WCFLOBAdapterInstaller action = new WCFLOBAdapterInstaller();  
            InstallContext context = new InstallContext();  
            // In the Setup project, this is set by selecting custom action  
            // and in Properties setting /INSTALLDIR="[TARGETDIR]\" for CustomActionData  
            context.Parameters.Add("INSTALLDIR", assemblyDirectory);  
            action.Context = context;  
            action.BeforeUninstallEventHandler(null, null);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="aa4f8-116">Si vous souhaitez découvrir un exemple d’adaptateur avec un package de déploiement, vous pouvez télécharger un adaptateur Echo terminé, y compris le script d’installation et de code de test.</span><span class="sxs-lookup"><span data-stu-id="aa4f8-116">If you want to explore a sample adapter with a deployment package, you can download a completed Echo Adapter including test code and installation script.</span></span> <span data-ttu-id="aa4f8-117">Cet exemple est fourni avec les fichiers d’installation de BizTalk à `\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples` ou `\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`.</span><span class="sxs-lookup"><span data-stu-id="aa4f8-117">This sample is included with your BizTalk installation files at `\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples` or `\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="aa4f8-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa4f8-118">See Also</span></span>  
 <span data-ttu-id="aa4f8-119">[Déployer un adaptateur à l’aide de l’adaptateur LOB WCF SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md) </span><span class="sxs-lookup"><span data-stu-id="aa4f8-119">[Deploy an adapter using the WCF LOB adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/deploy-an-adapter-using-the-wcf-lob-adapter-sdk.md) </span></span>  
 [<span data-ttu-id="aa4f8-120">Annuler le déploiement d’un adaptateur à l’aide de l’adaptateur LOB WCF SDK</span><span class="sxs-lookup"><span data-stu-id="aa4f8-120">Undeploy an adapter using the WCF LOB adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/undeploy-an-adapter-using-the-wcf-lob-adapter-sdk.md)
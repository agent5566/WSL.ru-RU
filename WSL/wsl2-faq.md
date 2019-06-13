---
title: Вопросы и ответы по WSL 2
description: Часто задаваемые вопросы о подсистеме Windows для Linux 2
keywords: BashOnWindows, bash, wsl, wsl2, windows, подсистема windows для linux, windowssubsystem, ubuntu, debian, suse, windows 10, установка
author: mscraigloewen
ms.author: mscraigloewen
ms.date: 05/30/2019
ms.topic: article
ms.assetid: 7afaeacf-435a-4e58-bff0-a9f0d75b8a51
ms.custom: seodec18
ms.openlocfilehash: 84805278abaeb6334c662e1dfab1bced3e0ddb0b
ms.sourcegitcommit: bb88269eb37405192625fa81ff91162393fb491f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2019
ms.locfileid: "67038094"
---
# <a name="wsl-2-faq"></a><span data-ttu-id="140d2-104">ЧАСТО ЗАДАВАЕМЫЕ ВОПРОСЫ О WSL 2</span><span class="sxs-lookup"><span data-stu-id="140d2-104">WSL 2 FAQ</span></span>

<span data-ttu-id="140d2-105">Ниже приведен список часто задаваемые вопросы (FAQ) о подсистеме Windows для Linux 2.</span><span class="sxs-lookup"><span data-stu-id="140d2-105">Below is a list of frequently asked questions (FAQ) about the Windows Subsystem for Linux 2.</span></span>

## <a name="does-wsl-2-use-hyper-v-will-it-be-available-on-windows-10-home"></a><span data-ttu-id="140d2-106">Используется ли WSL 2 Hyper-V?</span><span class="sxs-lookup"><span data-stu-id="140d2-106">Does WSL 2 use Hyper-V?</span></span> <span data-ttu-id="140d2-107">Он будет доступен в Windows 10 Домашняя?</span><span class="sxs-lookup"><span data-stu-id="140d2-107">Will it be available on Windows 10 Home?</span></span>

<span data-ttu-id="140d2-108">WSL 2 будут доступны во всех номерах SKU где WSL сейчас доступна, включая Windows 10 Домашняя.</span><span class="sxs-lookup"><span data-stu-id="140d2-108">WSL 2 will be available on all SKUs where WSL is currently available, including Windows 10 Home.</span></span>

<span data-ttu-id="140d2-109">Последняя версия WSL использует архитектуру Hyper-V его виртуализации.</span><span class="sxs-lookup"><span data-stu-id="140d2-109">The newest version of WSL uses Hyper-V architecture to enable its virtualization.</span></span> <span data-ttu-id="140d2-110">Эта архитектура будут доступны в дополнительный компонент, который представляет собой подмножество компонент Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="140d2-110">This architecture will be available in an optional component that is a subset of the Hyper-V feature.</span></span> <span data-ttu-id="140d2-111">Это необязательный компонент, будут доступны во всех номерах SKU.</span><span class="sxs-lookup"><span data-stu-id="140d2-111">This optional component will be available on all SKUs.</span></span> <span data-ttu-id="140d2-112">Вы сможете узнать больше о эта возможность скоро поближе к выпуску WSL 2.</span><span class="sxs-lookup"><span data-stu-id="140d2-112">You can expect to see more details about this experience soon as we get closer to the WSL 2 release.</span></span>

## <a name="what-will-happen-to-wsl-1-will-it-be-abandoned"></a><span data-ttu-id="140d2-113">Что произойдет с WSL 1?</span><span class="sxs-lookup"><span data-stu-id="140d2-113">What will happen to WSL 1?</span></span> <span data-ttu-id="140d2-114">Будет его брошенным?</span><span class="sxs-lookup"><span data-stu-id="140d2-114">Will it be abandoned?</span></span>

<span data-ttu-id="140d2-115">В настоящее время у нас есть не планируем отказаться от WSL 1.</span><span class="sxs-lookup"><span data-stu-id="140d2-115">We currently have no plans to deprecate WSL 1.</span></span> <span data-ttu-id="140d2-116">Можно запустить WSL 1 и WSL 2 дистрибутивов рядом друг с другом и можно обновить и понизить любого дистрибутива в любое время.</span><span class="sxs-lookup"><span data-stu-id="140d2-116">You can run WSL 1 and WSL 2 distros side by side, and can upgrade and downgrade any distro at any time.</span></span> <span data-ttu-id="140d2-117">Добавление WSL 2 в качестве новой архитектуры представляется более эффективную платформу для команды WSL для предоставления функций, которые делают WSL удивительные способ запустить среду Linux в Windows.</span><span class="sxs-lookup"><span data-stu-id="140d2-117">Adding WSL 2 as a new architecture presents a better platform for the WSL team to deliver features that make WSL an amazing way to run a Linux environment in Windows.</span></span>

## <a name="will-i-be-able-to-run-wsl-2-and-other-3rd-party-virtualization-tools-such-as-vmware-or-virtualbox"></a><span data-ttu-id="140d2-118">Я смогу выполнять WSL 2 и других сторонних виртуализации средств VMware или VirtualBox?</span><span class="sxs-lookup"><span data-stu-id="140d2-118">Will I be able to run WSL 2 and other 3rd party virtualization tools such as VMware, or VirtualBox?</span></span>

<span data-ttu-id="140d2-119">Некоторые сторонние приложения не может работать при использовании Hyper-V, это означает, что они не смогут при включении WSL 2.</span><span class="sxs-lookup"><span data-stu-id="140d2-119">Some 3rd party applications cannot work when Hyper-V is in use, which means they will not be able to run when WSL 2 is enabled.</span></span> <span data-ttu-id="140d2-120">К сожалению, это включает ли VMware и версии VirtualBox до VirtualBox 6 (VirtualBox 6.0.0, выпущенный в декабре 2018 [теперь поддерживает Hyper-V как базовая резервная выполнения на узле Windows] [ 1]!)</span><span class="sxs-lookup"><span data-stu-id="140d2-120">Unfortunately, this does include VMware, and versions of VirtualBox before VirtualBox 6 (VirtualBox 6.0.0 released in December 2018 [now supports Hyper-V as a fallback execution core on a Windows host][1]!)</span></span>

<span data-ttu-id="140d2-121">Мы изучаем способов, позволяющих устранить эту проблему.</span><span class="sxs-lookup"><span data-stu-id="140d2-121">We are investigating ways to help resolve this issue.</span></span> <span data-ttu-id="140d2-122">Например, мы предоставляем набор API, вызываемых [платформа низкоуровневой оболочки] [ 2] , виртуализации сторонних поставщиков можно использовать для обеспечения совместимости с Hyper-V программного обеспечения</span><span class="sxs-lookup"><span data-stu-id="140d2-122">For example, we expose a set of APIs called [Hypervisor Platform][2] that third-party virtualization providers can use to make their software compatible with Hyper-V’s.</span></span> <span data-ttu-id="140d2-123">Это позволяет приложениям использовать архитектуру Hyper-V для их эмуляции, например [эмулятор Android Google][3], и, и VirtualBox, 6 и более поздних версий, которая теперь она совместима с Hyper-V.</span><span class="sxs-lookup"><span data-stu-id="140d2-123">This lets applications use the Hyper-V architecture for their emulation such as [the Google Android Emulator][3], and VirtualBox 6 and above which are both now compatible with Hyper-V.</span></span>

## <a name="can-i-access-the-gpu-in-wsl-2-are-there-plans-to-increase-hardware-support"></a><span data-ttu-id="140d2-124">Получить доступ к GPU в WSL 2?</span><span class="sxs-lookup"><span data-stu-id="140d2-124">Can I access the GPU in WSL 2?</span></span> <span data-ttu-id="140d2-125">Планируется ли увеличить аппаратной поддержки?</span><span class="sxs-lookup"><span data-stu-id="140d2-125">Are there plans to increase hardware support?</span></span>

<span data-ttu-id="140d2-126">В начальными выпусками доступ к оборудованию WSL 2 Поддержка будет ограничена, например: вы не сможете доступа к GPU, последовательный или USB.</span><span class="sxs-lookup"><span data-stu-id="140d2-126">In initial releases of WSL 2 hardware access support will be limited, e.g: you will be unable to access the GPU, serial or USBs .</span></span> <span data-ttu-id="140d2-127">Однако добавление улучшения поддержки устройства велико в нашу невыполненную работу, как откроется многие дополнительные варианты использования для разработчиков, которым требуется взаимодействовать с этими устройствами.</span><span class="sxs-lookup"><span data-stu-id="140d2-127">However, adding better device support is high on our backlog, as this opens many more use cases for developers that wish to interact with these devices.</span></span> <span data-ttu-id="140d2-128">В то же время вы всегда можете использовать WSL 1, который имеет последовательный порт и доступа USB.</span><span class="sxs-lookup"><span data-stu-id="140d2-128">In the meantime, you can always use WSL 1 which has serial port and USB access.</span></span> <span data-ttu-id="140d2-129">. Следите за этот блог и WSL члены команды в Twitter для получения последних сведений о последних возможностях, ожидаемых в insider сборок и обратиться к Присылайте ваши отзывы о каких устройств, которые вы хотите взаимодействовать с!</span><span class="sxs-lookup"><span data-stu-id="140d2-129">Please stay tuned to this blog and WSL team members on Twitter to stay informed about the latest features coming to insider builds and reach out to give us feedback on what devices you’d like to interact with!</span></span>

## <a name="will-wsl-2-be-able-to-use-networking-applications"></a><span data-ttu-id="140d2-130">WSL 2 смогут использовать сетевые приложения?</span><span class="sxs-lookup"><span data-stu-id="140d2-130">Will WSL 2 be able to use networking applications?</span></span>

<span data-ttu-id="140d2-131">Да, в целом сети приложениях будет быстрее и лучше, поскольку у нас есть полный системный вызов совместимости.</span><span class="sxs-lookup"><span data-stu-id="140d2-131">Yes, in general networking applications will be faster and work better since we have full system call compatibility.</span></span> <span data-ttu-id="140d2-132">Тем не менее новая архитектура использует виртуализованные сетевые компоненты.</span><span class="sxs-lookup"><span data-stu-id="140d2-132">However, the new architecture uses virtualized networking components.</span></span> <span data-ttu-id="140d2-133">Это означает, что в первоначальных предварительных сборок WSL 2 будет вести себя подобно тому к виртуальной машине, например: WSL 2 будет иметь разные IP-адреса хост-компьютере.</span><span class="sxs-lookup"><span data-stu-id="140d2-133">This means that in initial preview builds WSL 2 will behave more similarly to a virtual machine, e.g: WSL 2 will have a different IP address than the host machine.</span></span> <span data-ttu-id="140d2-134">Мы стремимся сделать WSL 2 вы так же, как WSL 1 и включающий в себя улучшению нашей сети истории.</span><span class="sxs-lookup"><span data-stu-id="140d2-134">We are committed to making WSL 2 feel the same as WSL 1, and that includes improving our networking story.</span></span> <span data-ttu-id="140d2-135">Мы планируем добавить улучшения сразу же после можно получить, например для доступа к всех сетевых приложений из Linux или Windows, с помощью localhost.</span><span class="sxs-lookup"><span data-stu-id="140d2-135">We expect to add improvements as quickly as we are able to, such as accessing all networking apps from Linux or Windows using localhost.</span></span> <span data-ttu-id="140d2-136">Будет исправлена Дополнительные сведения о наших сетевых истории и усовершенствования, как мы используем подход выпуска WSL 2.</span><span class="sxs-lookup"><span data-stu-id="140d2-136">We will be posting more details about our networking story and improvements as we approach the release of WSL 2.</span></span>

## <a name="can-i-run-wsl-2-in-a-virtual-machine"></a><span data-ttu-id="140d2-137">Можно ли запускать WSL 2 на виртуальной машине?</span><span class="sxs-lookup"><span data-stu-id="140d2-137">Can I run WSL 2 in a virtual machine?</span></span>

<span data-ttu-id="140d2-138">Да!</span><span class="sxs-lookup"><span data-stu-id="140d2-138">Yes!</span></span> <span data-ttu-id="140d2-139">Необходимо убедиться, что виртуальная машина имеет вложенные виртуализация включена.</span><span class="sxs-lookup"><span data-stu-id="140d2-139">You need to make sure that the virtual machine has nested virtualization enabled.</span></span> <span data-ttu-id="140d2-140">Эту функцию можно включить в Hyper-V, выполнив следующую команду в окне PowerShell с правами администратора:</span><span class="sxs-lookup"><span data-stu-id="140d2-140">This can be enabled in Hyper-V by running the following command in a PowerShell window with Administrator privileges:</span></span>

`Set-VMProcessor -VMName <VMName> -ExposeVirtualizationExtensions $true`

<span data-ttu-id="140d2-141">Обязательно замените "&lt;VMName&gt;" с именем виртуальной машины.</span><span class="sxs-lookup"><span data-stu-id="140d2-141">Make sure to replace '&lt;VMName&gt;' with the name of your virtual machine.</span></span>

 [1]: https://www.virtualbox.org/wiki/Changelog-6.0
 [2]: https://docs.microsoft.com/en-us/virtualization/api/
 [3]: https://devblogs.microsoft.com/visualstudio/hyper-v-android-emulator-support/
local UserInputService = game:GetService("UserInputService")
local character = game.Players.LocalPlayer.Character or game.Players.LocalPlayer.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
local rootPart = character:WaitForChild("HumanoidRootPart")

local animationId1 = "rbxassetid://14809854900"
local animationId2 = "rbxassetid://15503060232"

local animation1 = Instance.new("Animation")
animation1.AnimationId = animationId1
local animationTrack1 = humanoid:LoadAnimation(animation1)

local animation2 = Instance.new("Animation")
animation2.AnimationId = animationId2
local animationTrack2 = humanoid:LoadAnimation(animation2)

local isPlayingAnimation1 = false
local isPlayingAnimation2 = false

local function playAnimation(animationId, stopTime, adjustSpeed)
    local animation = Instance.new("Animation")
    animation.AnimationId = animationId
    local animationTrack = humanoid:LoadAnimation(animation)
    animationTrack:Play()
    animationTrack:AdjustSpeed(adjustSpeed)
    animationTrack.TimePosition = stopTime
    return animationTrack
end

local function handleAnimationDetection(animSets)
    rootPart.Anchored = false

    local function onAnimPlayed(animationTrack)
        local animId = tonumber(string.match(animationTrack.Animation.AnimationId, "%d+"))

        for _, animSet in ipairs(animSets) do
            for _, stopId in ipairs(animSet.idsToStop) do
                if animId == stopId then
                    animationTrack:Stop()

                    if animSet.replacementAnimId ~= 0 then
                        local replacementAnimation = Instance.new("Animation")
                        replacementAnimation.AnimationId = "rbxassetid://" .. animSet.replacementAnimId
                        local newTrack = humanoid:LoadAnimation(replacementAnimation)
                        newTrack:Play()

                        -- Handle animation adjustments
                        if animSet.fasterAnimation2 then
                            newTrack:AdjustSpeed(1.15)
                        elseif animSet.fasterAnimation1 then
                            newTrack:AdjustSpeed(0.9)
                        elseif animSet.customAnimationSettings1 then
                            newTrack:AdjustSpeed(3.5)
                            newTrack.TimePosition = 1.5
                            wait(0.5)
                            newTrack:Stop()
                        elseif animSet.customAnimationSettings2 then
                            newTrack:Play()
                            newTrack:AdjustSpeed(0.5)
                            newTrack.TimePosition = 1.1
                            wait(1.5)
                            newTrack.TimePosition = 3
                            newTrack:AdjustSpeed(-0.5)
                            wait(1.55)
                            newTrack:Stop()
                        elseif animSet.downslamTimePosition then
                            newTrack:AdjustSpeed(1.5)
                        end
                        if animSet.slowerM1 then
                            newTrack:AdjustSpeed(0.8)
                        end
                        if animSet.customAnimationPosition1 then
                            newTrack:AdjustSpeed(0.8)
                            newTrack.TimePosition = 0.55
                        end
                    end

                    if animSet.anchorAfterReplacement then
                        rootPart.Anchored = true
                        wait(0.5)
                        rootPart.Anchored = false
                    end

                    if animSet.DeathCounterReplace then
                        local function ReplaceDeathCounterAnim()
                            print("Starting Death Counter animation")
                            local DeathCounterAnim = Instance.new("Animation")
                            DeathCounterAnim.AnimationId = "rbxassetid://16310343179"
                            local DeathCounterAnimTrack = humanoid:LoadAnimation(DeathCounterAnim)
        					DeathCounterAnimTrack:Play()
							DeathCounterAnimTrack.TimePosition = 2.25
							DeathCounterAnimTrack:AdjustSpeed(0.2)
							wait(2)
							DeathCounterAnimTrack:AdjustSpeed(0)
							wait(2)
							DeathCounterAnimTrack:AdjustSpeed(0.1)
							wait(0.5)
							DeathCounterAnimTrack:AdjustSpeed(0)
							wait(2)
							DeathCounterAnimTrack:AdjustSpeed(0.75)
                        end
                        spawn(ReplaceDeathCounterAnim)
                    end

                    if animSet.StoicBomb then
                        local function teleportPlayer()
                            print("Teleporting player")
                            local currentPosition = rootPart.Position
                            local currentOrientation = rootPart.CFrame - rootPart.Position -- Preserve orientation
                            local targetHeight = currentPosition.Y + 5000
                            rootPart.CFrame = CFrame.new(Vector3.new(currentPosition.X, targetHeight, currentPosition.Z)) * currentOrientation
                            wait(0.5)

                            while true do
                                local currentY = rootPart.Position.Y
                                print("Current Y:", currentY)

                                if currentY < 460 then
                                    rootPart.Anchored = true
                                    wait(3)
                                    rootPart.Anchored = false
                                    break
                                end

                                rootPart.CFrame = rootPart.CFrame - Vector3.new(0, 75, 0)
                                wait(0.1)
                            end
                            print("Teleporting complete")
                        end

                        local function playStoicBombAnimation()
                            print("Playing Stoic Bomb animation")
                            local StoicBombAnimation = Instance.new("Animation")
                            StoicBombAnimation.AnimationId = "rbxassetid://16524237104"
                            local StoicBombAnimationTrack = humanoid:LoadAnimation(StoicBombAnimation)
                            StoicBombAnimationTrack:Play()
                            wait(7)
                            StoicBombAnimationTrack:Stop()
                            print("Stoic Bomb animation finished")
                        end

                        -- Run both functions concurrently
                        coroutine.wrap(teleportPlayer)()
                        coroutine.wrap(playStoicBombAnimation)()
                    end

                    if animSet.UnlimitedFlexWorks then
                        local function UnlimitedFlexWorksReplaceAnim()
                            print("Starting Unlimited Flex Works animations")

                            local UnlimitedFlexWorksAnimPlay1 = playAnimation("rbxassetid://17086440627", 0, 1)
                            wait(5)
                            UnlimitedFlexWorksAnimPlay1:Stop()
                            print("Animation 1 finished")

                            local UnlimitedFlexWorksAnimPlay2 = playAnimation("rbxassetid://17105983229", 0, 5)
                            wait(0.5)
                            UnlimitedFlexWorksAnimPlay2:Stop()
                            print("Animation 2 finished")

                            local UnlimitedFlexWorksAnimPlay3 = playAnimation("rbxassetid://16023456135", 1, 0)
                            wait(6)
                            UnlimitedFlexWorksAnimPlay3:Stop()
                            print("Animation 3 finished")
                        end

                        coroutine.wrap(UnlimitedFlexWorksReplaceAnim)()
                    end

                    if animSet.FiveSeasons then
                        local function setFirstPersonView()
                            local player = game.Players.LocalPlayer
                            local camera = workspace.CurrentCamera
                            player.CameraMode = Enum.CameraMode.LockFirstPerson
                            camera.CameraType = Enum.CameraType.Custom
                        end

                        local function lookDown()
                            local rootPosition = rootPart.Position
                            workspace.CurrentCamera.CFrame = CFrame.new(rootPosition + Vector3.new(0, 5, 0), rootPosition)
                        end

                        local function restoreCameraControl()
                            local player = game.Players.LocalPlayer
                            local camera = workspace.CurrentCamera
                            player.CameraMode = Enum.CameraMode.Classic
                            camera.CameraType = Enum.CameraType.Custom
                        end

                        local function playAnimation(animationId, stopTime, adjustSpeed)
                            local animation = Instance.new("Animation")
                            animation.AnimationId = animationId
                            local animationTrack = humanoid:LoadAnimation(animation)
                            animationTrack:Play()
                            animationTrack:AdjustSpeed(adjustSpeed)
                            animationTrack.TimePosition = stopTime
                            return animationTrack
                        end

                        local function teleportToHeight(targetHeight)
                            rootPart.Anchored = true
                            while rootPart.Position.Y < targetHeight do
                                local currentPosition = rootPart.Position
                                local newCFrame = CFrame.new(currentPosition.X, currentPosition.Y + 5, currentPosition.Z)
                                rootPart.CFrame = newCFrame
                                wait(0.1)
                            end
                            rootPart.CFrame = CFrame.new(rootPart.Position.X, targetHeight, rootPart.Position.Z)
                            rootPart.Anchored = false
                        end

                        local function moveCharacter()
                            local movements = {20, -40, 20, 60, -90, 30}
                            local delayTime = 0.00005

                            for _, move in ipairs(movements) do
                                local currentPosition = rootPart.Position
                                local newCFrame = CFrame.new(currentPosition.X + move, currentPosition.Y, currentPosition.Z)
                                rootPart.CFrame = newCFrame
                                wait(delayTime)
                            end
                        end

                        local function increaseHeight()
                            print("Increasing height")
                            local firstAnimationTrack = playAnimation("rbxassetid://13047328208", 0.733, 0)
                            wait(1)
                            firstAnimationTrack:Stop()

                            local secondAnimationTrack = playAnimation("rbxassetid://16945557433", 0.5, 0)
                            teleportToHeight(500)

                            local endTime = tick() + 3
                            while tick() < endTime do
                                local currentPosition = rootPart.Position
                                if currentPosition.Y < 500 then
                                    rootPart.CFrame = CFrame.new(currentPosition.X, 500, currentPosition.Z)
                                end
                                wait(0.1)
                            end
                            wait(1)
                            secondAnimationTrack:Stop()
                            local thirdAnimationTrack = playAnimation("rbxassetid://13047366862", 0.5, 0)
                            moveCharacter()
                            wait(2)
                            thirdAnimationTrack:Stop()
                            print("Height increase finished")
                        end

                        increaseHeight()
                    end
                    break
                end
            end
        end
    end

    humanoid.AnimationPlayed:Connect(onAnimPlayed)
end

local animationSets = {
    {idsToStop = {10469493270}, replacementAnimId = 13532600125, slowerM1 = true},
    {idsToStop = {10469630950}, replacementAnimId = 13491635433, slowerM1 = true},
    {idsToStop = {10469639222}, replacementAnimId = 17889290569, slowerM1 = true},
    {idsToStop = {10469643643}, replacementAnimId = 13378751717, slowerM1 = true},
    {idsToStop = {10468665991}, replacementAnimId = 17838619895, fasterAnimation2 = true},
    {idsToStop = {10466974800}, replacementAnimId = 12273188754, fasterAnimation2 = true},
    {idsToStop = {10471336737}, replacementAnimId = 17838006839, customAnimationPosition1 = true},
    {idsToStop = {12510170988}, replacementAnimId = 14920779925, anchorAfterReplacement = true, customAnimationSettings1 = true},
    {idsToStop = {10470104242}, replacementAnimId = 17858878027, downslamTimePosition = true},
    {idsToStop = {15955393872}, replacementAnimId = 15997042291, customAnimationSettings2 = true},
    {idsToStop = {12447707844}, replacementAnimId = 15957376722},
    {idsToStop = {12983333733}, replacementAnimId = 0, UnlimitedFlexWorks = true},
    {idsToStop = {11343318134}, replacementAnimId = 0, DeathCounterReplace = true},
    {idsToStop = {11365563255}, replacementAnimId = 0, StoicBomb = true},
    {idsToStop = {13927612951}, replacementAnimId = 0, FiveSeasons = true},
}

handleAnimationDetection(animationSets)

local function teleportToHeight(targetHeight)
    local currentPosition = rootPart.Position
    local newCFrame = CFrame.new(currentPosition.X, targetHeight, currentPosition.Z)
    rootPart.CFrame = newCFrame
end

UserInputService.InputBegan:Connect(function(input, gameProcessedEvent)
    if gameProcessedEvent then return end

    if input.KeyCode == Enum.KeyCode.LeftBracket then
        if isPlayingAnimation1 then
            animationTrack1:Stop()
            isPlayingAnimation1 = false
        else
            animationTrack1:Play()
			animationTrack1.TimePosition = 1.6
            animationTrack1:AdjustSpeed(0.015)
            wait(5.5)
            animationTrack1:AdjustSpeed(0)
            isPlayingAnimation1 = true
        end
    elseif input.KeyCode == Enum.KeyCode.RightBracket then
        if isPlayingAnimation2 then
            animationTrack2:Stop()
            isPlayingAnimation2 = false
        else
            animationTrack2:Play()
            animationTrack2:AdjustSpeed(1)
            wait(8)
            animationTrack2:AdjustSpeed(0)
            isPlayingAnimation2 = true
        end
    elseif input.KeyCode == Enum.KeyCode.Equals then
        teleportToHeight(440)
    end
end)

local Player = game.Players.LocalPlayer
local ScreenGui = Instance.new("ScreenGui")
local TextButton = Instance.new("TextButton")
local SecondButton = Instance.new("TextButton")
local ThirdButton = Instance.new("TextButton")
local FourthButton = Instance.new("TextButton")
local TitleLabel = Instance.new("TextLabel")
local FooterLabel = Instance.new("TextLabel")
local BackgroundFrame = Instance.new("Frame")

-- GUI Ayarları
ScreenGui.Parent = Player:WaitForChild("PlayerGui")

-- Arka Plan Ayarları
BackgroundFrame.Size = UDim2.new(0.8, 0, 0.8, 0)
BackgroundFrame.Position = UDim2.new(0.5, -160, 0.5, -160)
BackgroundFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
BackgroundFrame.Parent = ScreenGui

-- Başlık Ayarları
TitleLabel.Size = UDim2.new(1, 0, 0, 30)
TitleLabel.Position = UDim2.new(0, 0, 0, 0)
TitleLabel.Text = "Gakra Hub"
TitleLabel.BackgroundTransparency = 1
TitleLabel.TextColor3 = Color3.fromRGB(173, 216, 230)
TitleLabel.Parent = BackgroundFrame

-- "İnf Combo" Buton Ayarları
TextButton.Size = UDim2.new(0, 150, 0, 40)
TextButton.Position = UDim2.new(0, 10, 0.4, -20)
TextButton.Text = "İnf Combo"
TextButton.BackgroundColor3 = Color3.fromRGB(144, 238, 144)
TextButton.TextColor3 = Color3.fromRGB(255, 0, 0)
TextButton.Parent = BackgroundFrame

-- İkinci Buton Ayarları
SecondButton.Size = UDim2.new(0, 150, 0, 40)
SecondButton.Position = UDim2.new(0, 10, 0.5, 10)
SecondButton.Text = "Unlock All Characters"
SecondButton.BackgroundColor3 = Color3.fromRGB(144, 238, 144)
SecondButton.TextColor3 = Color3.fromRGB(255, 0, 0)
SecondButton.Parent = BackgroundFrame

-- Üçüncü Buton Ayarları
ThirdButton.Size = UDim2.new(0, 150, 0, 40)
ThirdButton.Position = UDim2.new(1, -160, 0.4, -20)
ThirdButton.Text = "Increase Speed"
ThirdButton.BackgroundColor3 = Color3.fromRGB(144, 238, 144)
ThirdButton.TextColor3 = Color3.fromRGB(255, 0, 0)
ThirdButton.Parent = BackgroundFrame

-- Dördüncü Buton Ayarları
FourthButton.Size = UDim2.new(0, 150, 0, 40)
FourthButton.Position = UDim2.new(1, -160, 0.5, 10)
FourthButton.Text = "Increase Jump"
FourthButton.BackgroundColor3 = Color3.fromRGB(144, 238, 144)
FourthButton.TextColor3 = Color3.fromRGB(255, 0, 0)
FourthButton.Parent = BackgroundFrame

-- Footer Ayarları
FooterLabel.Size = UDim2.new(1, 0, 0, 30)
FooterLabel.Position = UDim2.new(0, 0, 1, -30)
FooterLabel.Text = "Made By: DoctorGakra"
FooterLabel.BackgroundTransparency = 1
FooterLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
FooterLabel.Parent = BackgroundFrame

-- Hareket Edebilirlik Ayarları
local function makeDraggable(element)
    local isDragging = false
    local startPos
    local dragInput

    element.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
            isDragging = true
            startPos = input.Position
            dragInput = input
        end
    end)

    element.InputChanged:Connect(function(input)
        if isDragging and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
            local delta = input.Position - startPos
            element.Position = UDim2.new(
                element.Position.X.Scale, 
                element.Position.X.Offset + delta.X, 
                element.Position.Y.Scale, 
                element.Position.Y.Offset + delta.Y
            )
            startPos = input.Position
        end
    end)

    element.InputEnded:Connect(function(input)
        if input == dragInput then
            isDragging = false
        end
    end)
end

-- Sadece arka plan için Dragging Fonksiyonunu Uygula
makeDraggable(BackgroundFrame)

-- Buton İşlevleri
TextButton.MouseButton1Click:Connect(function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Gakra12/Gakra12/refs/heads/main/%C4%B0nfCombo2"))()
end)

SecondButton.MouseButton1Click:Connect(function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/Gakra12/Gakra12/refs/heads/main/free"))()
end)

ThirdButton.MouseButton1Click:Connect(function()
    local player = game.Players.LocalPlayer
    if player.Character and player.Character:FindFirstChild("Humanoid") then
        player.Character.Humanoid.WalkSpeed = player.Character.Humanoid.WalkSpeed + 10 -- Her tıklamada yürüyüş hızını artır
    end
end)

FourthButton.MouseButton1Click:Connect(function()
    local player = game.Players.LocalPlayer
    if player.Character and player.Character:FindFirstChild("Humanoid") then
        player.Character.Humanoid.JumpPower = player.Character.Humanoid.JumpPower + 10 -- Her tıklamada zıplama gücünü artır
    end
end)

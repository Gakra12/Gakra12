local ScreenGui = Instance.new("ScreenGui")
local TextButton = Instance.new("TextButton")
local SecondButton = Instance.new("TextButton")
local ThirdButton = Instance.new("TextButton")
local FourthButton = Instance.new("TextButton")
local TitleLabel = Instance.new("TextLabel")
local FooterLabel = Instance.new("TextLabel") -- Yeni etiket
local BackgroundFrame = Instance.new("Frame")

-- GUI Ayarları
ScreenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Arka Plan Ayarları
BackgroundFrame.Size = UDim2.new(0.8, 0, 0.8, 0) -- Daha büyük arka plan
BackgroundFrame.Position = UDim2.new(0.5, -160, 0.5, -160) -- Merkeze yerleştirmek için ayarlandı
BackgroundFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0) -- Siyah arka plan
BackgroundFrame.Parent = ScreenGui

-- Başlık Ayarları
TitleLabel.Size = UDim2.new(1, 0, 0, 30)
TitleLabel.Position = UDim2.new(0, 0, 0, 0)
TitleLabel.Text = "Gakra Hub" -- Başlık yazısı
TitleLabel.BackgroundTransparency = 1 -- Arka planı şeffaf
TitleLabel.TextColor3 = Color3.fromRGB(173, 216, 230) -- Açık mavi metin
TitleLabel.Parent = BackgroundFrame

-- "İnf Combo" Buton Ayarları
TextButton.Size = UDim2.new(0, 150, 0, 40) -- Boyutu
TextButton.Position = UDim2.new(0, 10, 0.4, -20) -- Yukarı alındı
TextButton.Text = "İnf Combo" -- Buton üzerindeki yazı
TextButton.BackgroundColor3 = Color3.fromRGB(144, 238, 144) -- Açık yeşil arka plan
TextButton.TextColor3 = Color3.fromRGB(255, 0, 0) -- Kırmızı metin
TextButton.Parent = BackgroundFrame

-- İkinci Buton Ayarları
SecondButton.Size = UDim2.new(0, 150, 0, 40) -- Boyutu
SecondButton.Position = UDim2.new(0, 10, 0.5, 10) -- 1. butondan biraz daha aşağıda
SecondButton.Text = "Unlock All Characters" -- Buton üzerindeki yazı
SecondButton.BackgroundColor3 = Color3.fromRGB(144, 238, 144) -- Açık yeşil arka plan
SecondButton.TextColor3 = Color3.fromRGB(255, 0, 0) -- Kırmızı metin
SecondButton.Parent = BackgroundFrame

-- Üçüncü Buton Ayarları (arka planın en sağında)
ThirdButton.Size = UDim2.new(0, 150, 0, 40) -- Boyutu
ThirdButton.Position = UDim2.new(1, -160, 0.4, -20) -- En sağda
ThirdButton.Text = "Increase Speed" -- Buton üzerindeki yazı
ThirdButton.BackgroundColor3 = Color3.fromRGB(144, 238, 144) -- Açık yeşil arka plan
ThirdButton.TextColor3 = Color3.fromRGB(255, 0, 0) -- Kırmızı metin
ThirdButton.Parent = BackgroundFrame

-- Dördüncü Buton Ayarları (arka planın en sağında)
FourthButton.Size = UDim2.new(0, 150, 0, 40) -- Boyutu
FourthButton.Position = UDim2.new(1, -160, 0.5, 10) -- En sağda
FourthButton.Text = "Increase Jump" -- Buton üzerindeki yazı
FourthButton.BackgroundColor3 = Color3.fromRGB(144, 238, 144) -- Açık yeşil arka plan
FourthButton.TextColor3 = Color3.fromRGB(255, 0, 0) -- Kırmızı metin
FourthButton.Parent = BackgroundFrame

-- Footer Ayarları (alt yazı)
FooterLabel.Size = UDim2.new(1, 0, 0, 30) -- Boyutu
FooterLabel.Position = UDim2.new(0, 0, 1, -30) -- Alt kısımda
FooterLabel.Text = "Made By: DoctorGakra" -- Alt yazı
FooterLabel.BackgroundTransparency = 1 -- Arka planı şeffaf
FooterLabel.TextColor3 = Color3.fromRGB(255, 255, 255) -- Beyaz metin
FooterLabel.Parent = BackgroundFrame

-- Hareket Edebilirlik Ayarları (sadece arka plan için)
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

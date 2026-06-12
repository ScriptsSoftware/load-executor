print("🔄 [Load Executor] loading...")

local load = loadstring

local function loadExecutorScript()
local url = "https://example.com/script.lua"

print("🌐 Loading script from: " .. url)  

local success, result = pcall(function()  
    return game:HttpGet(url)  
end)  

if not success then  
    warn("❌ Error downloading script: " .. tostring(result))  
    return  
end  

print("✅ Script downloaded")  

local func = load(result)  

if type(func) == "function" then  
    func()  
    print("🚀 Script executed successfully")  
else  
    warn("❌ Error compiling script")  
    return  
end  

if syn and syn.toast_notification then  
    syn.toast_notification({  
        Title = "Load Executor",  
        Content = "Executor loaded successfully",  
        Duration = 6  
    })  
end

end

loadExecutorScript()

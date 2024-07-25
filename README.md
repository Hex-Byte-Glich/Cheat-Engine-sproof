# Cheat-Engine-sproof

function renameComponents(c)
    local i
    if c.Component then
      for i=0,c.ComponentCount-1 do
        renameComponents(c.Component[i])
      end
    end

    if c.Caption then
      c.Caption=string.gsub(c.Caption, "%s", "__")
      c.Caption=string.gsub(c.Caption, "e", "m")
    end
  end


  for i=0,getFormCount()-1 do
      local form = getForm(i)
      for j=0,form.ControlCount-1 do
        renameComponents(form)
      end

      form.Caption='Among Us Engine'
  end

  registerFormAddNotification(function(f)
    f.registerCreateCallback(function(frm)
      renameComponents(f)
    end)
  end)

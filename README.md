package fr.guitest.gui;

import net.minecraft.client.Minecraft;
import net.minecraft.client.gui.GuiButton;
import net.minecraft.client.gui.GuiScreen;
import net.minecraft.client.renderer.GlStateManager;
import net.minecraft.util.ResourceLocation;

public class GuiMain extends GuiScreen {
	
	private final ResourceLocation background = new  ResourceLocation("textures/gui/gui/GUI_Base (1).png");

	private final int xSize = 256;
	private final int ySize = 202;
	
	private int guiLeft;
	private int guiTop;
	
	private Minecraft minecraft;
	
	public GuiMain(Minecraft mc) {
		minecraft = mc;
	}

	
	public void initGui() {
		guiLeft = (this.width - this.xSize) / 2;
		guiTop = (this.height - this.ySize) / 2;
		
		buttonList.add(new GuiButton(0, guiLeft - 50, guiTop + 91, 100, 20,"premier button")); 
	}

	public void actionPerfonrmed(GuiButton button) {
		if(button.id == 0)
			this.mc.thePlayer.sendChatMessage("YO !");
	}
	
	public void drawScreen(int mouseX, int mouseY, float partialTicks) {
		
		drawBackgroundImage();
		super.drawScreen(mouseX, mouseY, partialTicks); 
	}
	
	public void drawBackgroundImage() {
		GlStateManager.pushMatrix();
		GlStateManager.color(1.0f, 1.0f, 1.0f, 1.0f);
		
		minecraft.getTextureManager().bindTexture(background);
		
		drawTexturedModalRect(guiLeft, guiTop, 0, 0, xSize, ySize);
		
		GlStateManager.popMatrix();
	}
	
}


import discord
from discord.ext import commands
import asyncio
from discord.ext import tasks

class Activity(commands.Cog):
    def __init__(self, bot):
        self.bot = bot
        self.update_activity.start()

    @commands.Cog.listener()
    async def on_ready(self):
        await self.update_activity()

    @tasks.loop(seconds=10)
    async def update_activity(self):
        if self.bot.is_ready():
            server_count = len(self.bot.guilds)
            total_member_count = sum(guild.member_count for guild in self.bot.guilds)

            activity1 = discord.CustomActivity(name="👦 × DerBoy")
            activity2 = discord.CustomActivity(name="⚙ × Beta Phase")
            activity3 = discord.CustomActivity(name=f"👥 × 103 User")
            activity4 = discord.CustomActivity(name=f"🔧 × Fettes Update vorbereitung")
            activity5 = discord.CustomActivity(name=f"🎧 × 2.1 Version")
            activity6 = discord.CustomActivity(name=f"🎉 × 100 Member geschaft")
            activity7 = discord.CustomActivity(name=f"🎉 × Brand neu!")
            await self.bot.change_presence(activity=activity1)
            await asyncio.sleep(5)
            await self.bot.change_presence(activity=activity2)
            await asyncio.sleep(5)
            await self.bot.change_presence(activity=activity3)
            await asyncio.sleep(5)
            await self.bot.change_presence(activity=activity4)
            await asyncio.sleep(5)
            await self.bot.change_presence(activity=activity5)
            await asyncio.sleep(5)
            await self.bot.change_presence(activity=activity6)
            await asyncio.sleep(5)
            await self.bot.change_presence(activity=activity7)
            await asyncio.sleep(5)
            
            
def setup(bot):
    bot.add_cog(Activity(bot))

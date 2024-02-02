# Kernel_bbb
Build kernel for bbb simplest

git clone https://github.com/RobertCNelson/bb-kernel 

cd bb-kernel/ 

git checkout origin/am33x-v5.4 -b tmp 
git checkout 24778dcbbf160be7985a6214daaf144083c77370

./build_kernel.sh 
 

vim KERNEL/drivers/watchdog/omap_wdt.c 
insert in function omap_wdt_probe(): 

static int omap_wdt_probe(struct platform_device *pdev) 
{ 
  printk(KERN_EMERG "Hello_Build: %s, %d\n", __func__, __LINE__); 
} 

./tools/rebuild.sh 

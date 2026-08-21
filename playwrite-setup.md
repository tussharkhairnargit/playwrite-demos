# Playwright CLI 
npm i -g @playwright/cli@latest
Refer :https://playwright.dev/agent-cli/introduction
npm init playwright@latest 
Refer : https://playwright.dev/docs/intro#installing-playwright

#configuration file name
playwright.config.ts

package.json - Dev Dependencies and script setup 
{
	"devDependencies":{
		"@playwrite/test": "^1.47.2",
		"@types/node":"^22.7.4"
	},
	main:"index.js"
	"scripts":{
		"test":npx playwright test",
		"test:chromium": "npx playwright --project chromium",
		"test:first":"npx playwright --grep @first",
		"test:local": "BASE_URL=http://localhost:4200 npx playwright test",
		"test:report": 
	}
}
# Commands 
npx playwright test --debug
npx playwrite test --headed 
npx playwrite test --project chromium 
npx playwrite test --project chromium -- project firefox
npx playwrite test --project "*omiun" // is it going to match with chromium
npx playwrite test test/example.spec.ts

To execute specific test we can tag - 
npx playwright test --grep @first

# Sample code 
test('has title', async ({ page})=> { 
	await page.goto('https://playwrite.dev/');
	await expect(page).toHaveTitle(/Playwrite/);
})

test('get started link', {tag:"@first"}, async({ page}) =>{
	await page.goto('https://playwrite.dev/');
	await page.getByRole('link',{ name: 'Get started'}).click();
})

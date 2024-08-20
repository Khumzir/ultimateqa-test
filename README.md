describe('Visit Automation Page', () => {
    it("ViewAutomationPage", () => {   
        cy.visit("https://ultimateqa.com/automation/")
        it("window width and height", () => {
        cy.viewport(1920, 1080)
        })
     })

     it('Get Page Title', () => {
        cy.visit("https://ultimateqa.com/automation/")
        cy.get('title').should('contain', 'Automation Practice - Ultimate QA')
        cy.screenshot()
     })

     it('Check page for Login Automation text and Login Test', () => {
        cy.visit("http://courses.ultimateqa.com/users/sign_in")
        cy.get("[name='user[email]']").type("khumzir@gmail.com")
        cy.get("[name='user[password]']").type("!Flowers123")
        cy.get("button[type='submit']").click()
        cy.get('h2').should('contain', 'Product')
          .log('Login to the application is successful')
     })

     it('Logout from page', () => {
        cy.visit('https://courses.ultimateqa.com/collections')
        cy.get('.header__nav-item > a').should('contain', 'Sign In')
          .log('Log out successful')
     })

     it('Browse to "Fill out forms" and Complete all forms', () => {
        cy.visit('https://ultimateqa.com/automation/')
        cy.get('title').should('contain', 'Automation Practice - Ultimate QA')
        cy.visit("https://ultimateqa.com/filling-out-forms/")
        cy.get('#et_pb_contact_name_0').type('Khumzi')
        cy.get('#et_pb_contact_message_0').type('It is with great appreciation that I will be joining VOSS Solutions QA team.')
        cy.get('#et_pb_contact_form_0 > .et_pb_contact > .et_pb_contact_form > .et_contact_bottom_container > .et_pb_contact_submit').click()
        cy.get('#et_pb_contact_name_1').type("Sakhumzi Rawana")
        cy.get('#et_pb_contact_message_1').type("To VOSS Solutions, I Thank you for welcoming me to your team. I feel welcomed!!!")
        cy.get('.clearfix > .input').type('19')
        cy.get('#et_pb_contact_form_1 > .et_pb_contact > .et_pb_contact_form > .et_contact_bottom_container > .et_pb_contact_submit').click()
        cy.get('.et-pb-contact-message > p').should('be.visible')
          .log('Forms submitted successful')
     })

     it('Browse to the "Fake Pricing Page" and Purchase the Basic package', () => {
        cy.visit('https://ultimateqa.com/automation/')
        cy.visit("https://ultimateqa.com/automation/fake-pricing-page/")
        cy.get('h1').should('be.visible')
        cy.get('.et_pb_column_2 > .et_pb_with_border > .et_pb_pricing_table_wrap > .et_pb_pricing_table > .et_pb_button_wrapper > .et_pb_button').click()
        .log('Purchased the Basic package successfully')
     })
})

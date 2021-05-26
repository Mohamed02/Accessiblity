ACCESSIBLITY of APPLICATION:

  Accessiblity is the concept that making an application accessible for all types of user irrespecive of their impairment or disablity. The disablity include visual(both blind 
  and one wiht color contrast issues),auditory, Congnitory, motor impairments, dexterity impairment
  broker wrist, dyslexia etc.
  
  ON a highlevel we have to takecare following items to make teh web app accessible
    1. Must have a sensible DOM ORDER
    2. FOCUS ing on required elments
    3. usage of SEMANTICS tags wheever necessary
    4. Able to navigage through the page via Keyboard
    5. LABELLING links,images appropriately


  
WebContent Accessiblity Guideline2.0 (WCAG)

It is the guildelien of best practices


  Three main topics that roll around Accessiblity are 

        FOCUS- Keyboard focus
        SEMANTICS- 
        STYLING and VISUAL DESIGN

FOCUS:

      For the users using Keyboard to navigate through a page requires the App should be FOUCS compliant

      Tab key - to move to next field
      shif+ tab key - to move to the previous field
      up + down array- to scroll across the values in teh field.

      Only field which the users can interact are added in teh taborder implicitly and thus making 
      it focussable. The static texts, headings, paragraphs are not focussable.

    DOM ORDER & VISUAL ORDER

      In most of the cases the dom order and and the visual order of elments will be same, But in Some scenarios, when we user
      css styling to move the position of the elment then the visual order and the DOM order will be different.

      The keyboard taborder will always in the order of the DOM. Hence it is recommended to have visual order and Tab order to be same

      if the are different due to desing,  then we have to use the html tag property called tabindex to make the tab order properl

      the element with taborder 0 will added in teh tab order list and it can foccused through scripts
      the elmenet with taborder -1 will not be included in the taborder list and 
      instead it can only be focussed through javascript. 
      Also taborder -1 is used when we wanted to focuss elments out of our dom. such as modal window etc.

      if the tabindex is greater than 0 then , then element will be added to the front of the list
      it is not recommended to have a tabindex greater than 0.

  SKIP LINK:

      Let us say if we have lots of links in the page header and if we wanted to get teh focus on the main content 
      of the page, then we have to strike the tab button multiple time before the tab goes to the main content.


      is those scenarios, we can use the skip link to skipp to the main content using an anchor tag with href as id of the main content div element.



    Roving over Radio buttons using Javascript
      Refer ud891-gh-pages/lesson2-focus/05-radio-group/solution/index.html

    How to avoid focussing elments which are offscreen ?
    If web app have a left side drawer (hide and collapse) which displays all the navigation option, then while hitting the tab on them keyboard
    will take you tab focus to the all the navs on the left panel. but it will be hidden for the user (that is , it is an offscreen content). this is not an appropritate behaviour.
    So Better hide the drawer using style display:none or visiblity hidden and then change it to block.

    So if you want to hide an element hide it direclty usign hidden, or display none, thus it wont be readable by screen reader.
    But dont hide it indirectly through opacity or z index, because though it is invisible, the screen reader will read it.

    you can use document.activeElement to find element which are currently focussed.


  Keyboard Trap:

    This is situation when the focus is on a component and it doesnt come outside irrespecive of how many tab you press.
    For e.g let us say if we have a dropdown with autocomplete and after you selected one ofthe option , and then select tab
    it wont come out of compnent. This is called keyboard trap.

    Though this is not desirable for this component , this is required when you open a modal window, where when you focus must
    always be inside the modal.


SEMANTICS:

    With help of screen reader we can determine followin details of a component in the following order
    1. Role: What type of the field it is , wether it is combo box, text field, radio button
    2. Name: What is the name of the field such as first name, last name
    3. State: Such as collapsed, Selected,
    4. Value: the value of the field


    In the most of the case Label replaces teh Name.
    The label can be a visible label(for text fields) or it can be text alternative in case of images.


  Where you have a checkbox in your page, then surround it by label . so that the checkbox gets clicked even when you 
  click on the label.

  When you have a button on the UI which a user could click on it.. Dont create that button with div element, it will be 
  difficult for the screen reader to read. You have to use button elmenet.

  Use H1, H2, H3 for headings instead of div

  whever you use an anchor tag . it should have an href attribute. Even if the anchor tag is not going to an external link
  it is must to have atleast teh href as href="#internaliD"  do not code it as below

   <a onclick="someFunction();"><a/>

   <button class="link">test</button>    //here link gives teh styling as a link 

   <a href="/"> <img src="asdfasdf"/> </a>


  simillary to get a checkbox ..use slect box and not imitate checkbox behaviour with a div element.

   The link text should be intuitive that it should say what is is supposed to do.

   use HTML5 semantics tag such as header, footer, main , nav , section which help screen reader  to read it in a much more meanignful way.

  
ARIA attributes:

        Aria attributes can modify the semantic information on the field. with these attributes we can information to the field which the html tags cannot add

        if you use custom fields rather than native fields it is recommended to have explicit aria attributes on the field for the screen reader to read the role and state of the field

        custom checkboxes are constructed with div , where as native checkboxes are constructed with input tag of type check box

        <div aria-checked="true" role="checkbox"></div>

        we have other attributes such as 

          aria-expanded
          aria-pressed
          aria-label
          aria-labbelledby  - its value is the id of the element whcih has the label in it
          aria-describedby - its value is the id of the element whcih has the description in it
          aria-posinset- position of the element in the section
          aria-setsize - size of the set
      aria-owns: It is used to represent a part of the dom (which is under different parent) as a sub content

      aria-activedescendent: IT tell id of the element inside the parent  must be focussed.
      aria-hidden: we can hide a some of the content to be read by screen reader such as graphs or charts using aria hidden attribute.
      aria-live: It is used to reprent an element which is live and loaded through live streaming such as notificaiton
      aria-atomic:
      aria-relevent:

STYLING:
        styling the web pages to support web accessiblity,

        we can add style based on aria attribute

        .toggle[aria-pressed="true"]{
          
        }
# Elsewhere

Web prototype for **Elsewhere**, a CS 147 (Autumn 2026) project. Elsewhere helps you turn an unexpected free hour into a small outing nearby, on a budget you set, with the friends you actually want to see.

**Live prototype:** https://romina-jately.github.io/elsewhere-prototype/

The deployed web build reuses the React Native screens, styles, and state logic from `heuristic-fixes` at `f3cda67`. GitHub Pages serves the self-contained `index.html` build from the root of `main`, with its styles, scripts, fonts, and place photographs bundled in the page.

---

## Access and setup

Open the link above in any modern browser (Chrome, Safari, Firefox or Edge). There is nothing to install and no account is needed.

- **Login:** the first screen asks for an email and password. Any email in a valid format (for example `test@stanford.edu`) and any password will log you in. "Create an account" skips the login check entirely.
- **No data is collected.** Nothing you type is sent anywhere or saved. Everything lives in the open browser tab, and refreshing the page starts the prototype over from the login screen.

## Device

Use the bottom tabs to navigate. The layout fills a phone screen and is centered at phone width on larger displays.

## Context

Elsewhere is meant to break up the monotony of a routine week and add spontaneity to it. Choose an open time window to plan a nearby outing and see it under Calendar in your profile. You can go alone, or let Elsewhere quietly check whether someone in your chosen circle of friends wants to do the same thing at the same time. If the interest is mutual, it's a match and you both get the plan. Your interest stays private unless it's mutual.

A user should be able to complete three tasks:

1. **Simple:** Explore a spontaneous event for an unexpected free hour.
2. **Moderate:** Decide how much you are willing to spend on your spontaneous activities, and update your preferences in the budget tab.
3. **Complex:** Prioritize matching for spontaneous activities with the friends that you are closest to.

## How to operate the prototype

The bottom tab bar has **Home, Discover, Circles, Budget and Profile**. Everything on screen responds to taps: buttons, toggles, search fields, filters and list rows.

**Getting in**
1. Log in with any email and password, or tap **Create an account**.
2. Pick at least one interest and tap **Continue**.
3. Optionally tap **Sync Contacts** and **Allow** to see demo contacts. Select friends and tap **Finish → Home**, or tap **Skip for now**.

**Task 1 (Simple): explore a spontaneous event for an unexpected free hour**
1. On **Home**, the quick picks are ranked by the interests you chose, each with the reason ("Because you like Cafés"). Tap one, or tap **Explore Nearby**.
2. **Discover** is the browsing page: a featured pick for you, search, filters (estimated price per person and walking time) and every place nearby. Tap a place.
3. That opens the **place details** page: photo, walk time, estimated price, duration, accessibility information, location, and visit history. Expand **Travel options** for walking, transit or driving routes in Maps, or tap **Plan a Visit**.
4. Choose **Go solo** or **See who's interested**, then enter a date, start time, and duration. The planner checks for past times, insufficient time for the visit, and conflicts with plans already made in Elsewhere. Include travel time for your route and optionally enter a different planned spending amount, including $0. For the friend option:
   - pick one or more circles and tap **Find a match**;
   - if someone in that circle also wants to go, you see **It's a match!**; tap **Confirm meetup**;
   - if no one does (or the circle is empty), you see **No one's free for this one**, with **Go solo instead**, **Change selected circles**, or **Tell me if someone’s in**.
   - To see each outcome: Mini Golf Tour with Close Friends matches with Jake; Bookstore with Close Friends finds no one; Bookstore with Friends matches with Tom.
5. Home shows the next confirmed outing in a banner above the scrollable content. Profile lists confirmed plans under Calendar.

**Task 2 (Moderate): update your spending preferences**
1. Open **Budget** to see per-person spending preferences.
2. Drag each category slider to choose a price tier from **$** to **$$$$**. Keyboard users can use the arrow keys.
3. The prototype applies your preferences immediately when recommending places.

**Task 3 (Complex): prioritize matching with close friends**
1. Open the **Circles** tab (**My Circles**). You start with three circles: Close Friends, Friends and Acquaintances.
2. Tap a circle (or its pencil icon) to edit it. Search your friends and check or uncheck people.
3. Tap **Save circle** to see the circle summary. Before saving, review the resulting members in each affected circle. Only you can see your circles. A person can only be in one circle, so adding someone moves them out of their old one.
4. **My Friends** lists everyone with their circle, **Add friends** adds suggested contacts and **Remove** optionally takes a friend out of your list and their circle.
5. Open an outing and choose **Plan a Visit → See who's interested**. Set your availability, choose **Close Friends**, and tap **Find a match**. Only friends in the selected circle are eligible to match.

**Profile**
- **Your map:** an interactive campus map with pins, visit counts, and a line connecting visits. Drag to pan, use the zoom controls, and tap a pin to see the place. Switch to **List** for a dated history. Tap any place to open it.
- **Interests:** tap **Edit** to change them. Home and Discover reorder right away.
- **Calendar:** set availability and review confirmed outings.
- **Settings:** a free-time nudges switch, your budget, and **Log out**.

## Tools used to build the prototype

- **Figma Design:** all screens, components, colors and type were designed in Figma. This includes the revisions from our lo-fi testing, such as adding a dedicated Budget tab to the footer so changing your budget is more intuitive.
- **React Native Web:** renders the app’s React Native components and styling in a browser. The web build adds browser sliders, map gesture handling, and share support.
- **Claude (Anthropic's AI assistant):** used to read the Figma file and generate the coded version of our screens and flows.
- **Lucide** icons and the **DM Sans / DM Serif Display** fonts (Google Fonts), matching the Figma design.
- **GitHub Pages** hosts the live link.

## Limitations and why

This is a medium-fidelity prototype, so there is no backend, no real accounts, and no connection to live users or calendar accounts. We wanted testers to experience the app as it would feel to use, rather than clicking only the hotspots we expected them to, so every control on screen does something. Where a real feature would need live data, other users or third-party services, we simulated it (Wizard of Oz) or used fixed data (hard-coded). This let us test the three task flows without building infrastructure that a medium-fidelity prototype doesn't call for.

### Wizard of Oz techniques

- **Mutual matching:** there are no other users. After **Find a match**, a "Checking your circle…" screen shows briefly. Each fake friend has a fixed list of places they "want to try"; if someone in the circle you chose has this place on their list, it's a match, otherwise you get the no-match screen. No one is actually asked.
- **Directions:** opens Google Maps with the example place as a search term.
- **Forgot password:** confirms that the reset is simulated.
- **Share:** opens the device’s share sheet when supported and otherwise copies the outing to the clipboard.
- **Free-time nudges:** the switch changes its state, but no notifications are sent.

### Hard-coded items

- **Login:** any valid-looking email and any password are accepted. Nothing is checked against real accounts or stored.
- **Places:** five fixed places (Matcha Café, Art Gallery, Bookstore, Mini Cat Town, Mini Golf Tour), with example walking times, estimated prices and photos. Matcha Café’s step-free entrance label is sample data. The other places show wheelchair access as unknown.
- **Recommendations:** each place has two fixed interest tags (Matcha Café: Cafés, Food · Art Gallery: Art, Events · Bookstore: Cafés, Art · Mini Cat Town: Cafés, Wellness · Mini Golf Tour: Outdoors, Events). Home and Discover rank places by how many tags match your interests and try to cover each interest at least once; ties go to the closer place. "Surprise me" favors places you haven't been. Music has no matching place yet.
- **Maps:** campus maps use OpenStreetMap tiles and fixed demo venue positions.
- **Visit history:** Profile starts with six example visits (Oct 3 to Oct 24) so the map isn't empty. Newly confirmed outings appear in the Calendar section.
- **Friends and contacts:** four starting friends (Tom, Jake, Sarah, Lynn) and four suggested contacts (Maya, Jess, Alex, Sophie). The contact permission and results are simulated. Starting circles are Close Friends (Jake, Lynn), Friends (Tom, Sarah) and Acquaintances (empty).
- **Budget:** spending tiers are set by category. A confirmed visit uses your entered amount or the sample estimate ($8, $15, or $0).
- **Session only:** nothing persists. Refreshing the page resets everything.

# Elsewhere

Medium-fidelity prototype for **Elsewhere**, a CS 147 (Autumn 2026) project. Elsewhere helps you turn an unexpected free hour into a small outing nearby, on a budget you set, with the friends you actually want to see.

**Live prototype:** https://romina-jately.github.io/elsewhere-prototype/

---

## Access and setup

Open the link above in any modern browser (Chrome, Safari, Firefox or Edge). There is nothing to install and no account is needed.

- **Login:** the first screen asks for an email and password. Any email in a valid format (for example `test@stanford.edu`) and any password will log you in. "Create an account" skips the login check entirely.
- **No data is collected.** Nothing you type is sent anywhere or saved. Everything lives in the open browser tab, and refreshing the page starts the prototype over from the login screen.
- **Reset:** on desktop, the **Reset prototype** button under the screen list returns everything to its starting state without a refresh.

## Device

The app is designed for a phone (the screens are 370 × 760, matching our Figma frames).

- **Recommended for testing: a laptop or desktop.** The phone screen appears in the middle of the page, and a panel on the left lists the three tasks with links that jump straight to any screen. This is the easiest way to follow and grade the task flows.
- **Phone:** opening the same link on a phone fills the whole screen, so it feels like the real app. The task panel is hidden on phones, so use the in-app tabs to move around.

## Context

Elsewhere is meant to break up the monotony of a routine week and add spontaneity to it. Choose an open time window to plan a nearby outing, then export the confirmed visit to your calendar. You can go alone, or let Elsewhere quietly check whether someone in your chosen circle of friends wants to do the same thing at the same time. If the interest is mutual, it's a match and you both get the plan. Your interest stays private unless it's mutual.

A user should be able to complete three tasks:

1. **Simple:** Explore an outing for an unexpected free hour. Find an outing for an unexpected free hour.
2. **Moderate:** Set a daily, weekly, or monthly budget. Choose a period and amount, then save.
3. **Complex:** Organize friends into circles. Manage selections and understand group changes.

## How to operate the prototype

The bottom tab bar has **Home, Discover, Circles, Budget and Profile**. Everything on screen responds to taps: buttons, toggles, search fields, filters and list rows.

**Getting in**
1. Log in with any email and password, or tap **Create an account**.
2. Pick at least one interest and tap **Continue**.
3. Optionally select friends to add, then tap **Finish** (or **Skip for now**).

**Task 1 (Simple): explore an outing for an unexpected free hour**
1. On **Home**, the quick picks are ranked by the interests you chose, each with the reason ("Because you like Cafés"). Tap one, or tap **Explore Nearby**.
2. **Discover** is the browsing page: a featured pick for you, search, filters (estimated price per person and walking time) and every place nearby. Tap a place.
3. That opens the **place details** page: photo, walk time, estimated price, duration, accessibility information, location, and visit history. Expand **Travel options** for walking, transit or driving routes in Maps, or tap **Plan a Visit**.
4. Choose **Go solo** or **See who's interested**, then enter a date, start time, and duration. The planner checks for past times, insufficient time for the visit, and conflicts with plans already made in Elsewhere. Include travel time for your route and optionally enter a different planned spending amount, including $0. For the friend option:
   - pick a circle and tap **Find a match**;
   - if someone in that circle also wants to go, you see **It's a match!**; tap **Confirm meetup**;
   - if no one does (or the circle is empty), you see **No one's free for this one**, with **Go solo instead**, **Try another circle**, or **Save interest for this time**.
   - To see each outcome: Mini Golf Tour with Close Friends matches with Jake; Bookstore with Close Friends finds no one; Bookstore with Friends matches with Tom.
5. Home shows the next confirmed outing in a banner above the scrollable content. Profile lists plans under Calendar, with a downloadable calendar file (.ics). Import it into your calendar app to add the visit.

**Task 2 (Moderate): set a budget**
1. Open the **Budget** tab. Switch between **Daily, Weekly and Monthly** to see each period's spending ring and categories.
2. Tap **Edit Budget**. Enter an amount or choose a preset ($0, $25, $50, $75).
3. Tap **Save changes**. The confirmation screen shows the new limit and what's left for the period. The summary shows total spent plus planned spending, remaining funds, and any overage.
4. The totals include sample spending and amounts planned for confirmed visits scheduled in the selected period.

**Task 3 (Complex): organize friends into circles**
1. Open the **Circles** tab (**My Circles**). You start with three circles: Close Friends, Friends and Acquaintances.
2. Tap a circle (or its pencil icon) to edit it. Search your friends and check or uncheck people.
3. Tap **Save circle** to see the circle summary. Before saving, review the resulting members in each affected circle. Only you can see your circles. A person can only be in one circle, so adding someone moves them out of their old one.
4. **My Friends** lists everyone with their circle, **Add friends** adds suggested contacts and **Remove** optionally takes a friend out of your list and their circle.
5. Circles feed back into Task 1: only people in the circle you pick can match with you.

**Profile**
- **Your map:** a map of campus showing every place you've been. Bigger circles mean more visits, a line traces the order you went, and dashed circles are places you haven't tried. Switch to **List** for a dated history. Tap any place to open it.
- **Interests:** tap **Edit** to change them. Home and Discover reorder right away.
- **Calendar:** set availability and download a calendar file for a confirmed plan.
- **Settings:** a free-time nudges switch, your budget, and **Log out**.

## Tools used to build the prototype

- **Figma Design:** all screens, components, colors and type were designed in Figma. This includes the revisions from our lo-fi testing, such as adding a dedicated Budget tab to the footer so changing your budget is more intuitive.
- **HTML, CSS and JavaScript:** the Figma screens were rebuilt as a single self-contained web page (`index.html`) so that every control works and the prototype keeps state between screens. Layout, colors and copy were taken directly from the Figma file.
- **Claude (Anthropic's AI assistant):** used to read the Figma file and generate the coded version of our screens and flows.
- **Lucide** icons and the **DM Sans / DM Serif Display** fonts (Google Fonts), matching the Figma design.
- **GitHub Pages** hosts the live link.

## Limitations and why

This is a medium-fidelity prototype, so there is no backend, no real accounts, and no connection to live users or calendar accounts. Calendar export creates a local .ics file. We wanted testers to experience the app as it would feel to use, rather than clicking only the hotspots we expected them to, so every control on screen does something. Where a real feature would need live data, other users or third-party services, we simulated it (Wizard of Oz) or used fixed data (hard-coded). This let us test the three task flows without building infrastructure that a medium-fidelity prototype doesn't call for.

### Wizard of Oz techniques

- **Mutual matching:** there are no other users. After **Find a match**, a "Checking your circle…" screen shows briefly. Each fake friend has a fixed list of places they "want to try"; if someone in the circle you chose has this place on their list, it's a match, otherwise you get the no-match screen. No one is actually asked.
- **Directions:** opens Google Maps with the example place as a search term.
- **Forgot password:** shows "Reset link sent" without sending an email.
- **Share:** copies a sample invite message to the clipboard instead of opening a share sheet.
- **Free-time nudges:** the switch changes its state, but no notifications are sent.

### Hard-coded items

- **Login:** any valid-looking email and any password are accepted. Nothing is checked against real accounts or stored.
- **Status bar:** always shows 9:41 and 100%.
- **Places:** five fixed places (Matcha Café, Art Gallery, Bookstore, Mini Cat Town, Mini Golf Tour), with example walking times, estimated prices and photos. Matcha Café’s step-free entrance label is sample data. The other places show wheelchair access as unknown.
- **Recommendations:** each place has two fixed interest tags (Matcha Café: Cafés, Food · Art Gallery: Art, Events · Bookstore: Cafés, Art · Mini Cat Town: Cafés, Wellness · Mini Golf Tour: Outdoors, Events). Home and Discover rank places by how many tags match your interests and try to cover each interest at least once; ties go to the closer place. "Surprise me" favors places you haven't been. Music has no matching place yet.
- **Maps:** the campus maps are a stylized drawing of our Figma map, not a real map. Place positions on it are fixed.
- **Visit history:** Profile starts with six example visits (Oct 3 to Oct 24) so the map isn't empty. Newly confirmed outings appear in the Calendar section.
- **Friends and contacts:** four starting friends (Tom, Jake, Sarah, Lynn) and four suggested contacts (Maya, Jess, Alex, Sophie). There is no contact sync. Starting circles are Close Friends (Jake, Lynn), Friends (Tom, Sarah) and Acquaintances (empty).
- **Budget:** default limits are $10 daily, $50 weekly and $200 monthly, each with example spending already logged. Each confirmed visit uses your entered amount or the sample estimate ($8, $15, or $0).
- **Session only:** nothing persists. Refreshing the page resets everything.

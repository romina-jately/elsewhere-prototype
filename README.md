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

Elsewhere is meant to break up the monotony of a routine week and add spontaneity to it. It links to your calendar, notices short or unexpected gaps in your day ("You have 1 hour free!"), and suggests things to do nearby in that window. You can go alone, or let Elsewhere quietly check whether someone in your chosen circle of friends wants to do the same thing at the same time. If the interest is mutual, it's a match and you both get the plan. Your interest stays private unless it's mutual.

A user should be able to complete three tasks:

1. **Simple:** explore a spontaneous event for an unexpected free hour.
2. **Moderate:** set a daily, weekly or monthly budget they're willing to stick to for spontaneous events.
3. **Complex:** organize friends into circles so they prioritize hanging out with the people they actually want to spend time with.

## How to operate the prototype

The bottom tab bar has **Home, Discover, Circles, Budget and Profile**. Everything on screen responds to taps: buttons, toggles, search fields, filters and list rows.

**Getting in**
1. Log in with any email and password, or tap **Create an account**.
2. Pick at least one interest and tap **Continue**.
3. Optionally select friends to add, then tap **Finish** (or **Skip for now**).

**Task 1 (Simple): explore a spontaneous event**
1. On **Home**, tap **Explore Nearby**, or tap one of the quick picks.
2. On **Discover**, search or use the filter button (price, walking time), then tap a place.
3. On the place card, tap **Plan a Visit**.
4. Choose **Go solo** to go straight to a confirmation, or **See who's interested** to try a hangout:
   - pick a circle and tap **Find a match**;
   - after a short search you see **It's a match!**; tap **Confirm meetup**.
5. The confirmed plan appears on Home ("Next up"), in Profile under Calendar, and on your map in Profile.

**Task 2 (Moderate): set a budget**
1. Open the **Budget** tab. Switch between **Daily, Weekly and Monthly** to see each period's spending ring and categories.
2. Tap **Edit Budget**. Choose a preset ($25, $50, $75), adjust with **− / +** in $5 steps, or tap **Custom** and type an amount.
3. Tap **Save changes**. The confirmation screen shows the new limit and what's left for the period. Saving without choosing an amount shows "Please choose an amount."
4. Visits you confirm in Task 1 add their cost to the matching category, so the ring updates.

**Task 3 (Complex): organize friends into circles**
1. Open the **Circles** tab (**My Circles**). You start with three circles: Close Friends, Friends and Acquaintances.
2. Tap a circle (or its pencil icon) to edit it. Search your friends and check or uncheck people.
3. Tap **Done** to see the circle summary. A person can only be in one circle, so adding someone moves them out of their old one.
4. **My Friends** lists everyone with their circle, and **Add friends** adds suggested contacts.
5. Circles feed back into Task 1: only people in the circle you pick can match with you.

**Profile**
- **Your map:** a map of campus showing every place you've been. Bigger circles mean more visits, a line traces the order you went, and dashed circles are places you haven't tried. Switch to **List** for a dated history. Tap any place to open it.
- **Interests:** tap **Edit** to change them.
- **Calendar:** a sync switch and your upcoming plans, each with an **Add** button.
- **Settings:** a free-time nudges switch, your budget, and **Log out**.

## Tools used to build the prototype

- **Figma Design:** all screens, components, colors and type were designed in Figma. This includes the revisions from our lo-fi testing, such as adding a dedicated Budget tab to the footer so changing your budget is more intuitive.
- **HTML, CSS and JavaScript:** the Figma screens were rebuilt as a single self-contained web page (`index.html`) so that every control works and the prototype keeps state between screens. Layout, colors and copy were taken directly from the Figma file.
- **Claude (Anthropic's AI assistant):** used to read the Figma file and generate the coded version of our screens and flows.
- **Lucide** icons and the **DM Sans / DM Serif Display** fonts (Google Fonts), matching the Figma design.
- **GitHub Pages** hosts the live link.

## Limitations and why

This is a medium-fidelity prototype, so there is no backend, no real accounts, and no connection to other users, calendars or maps. We wanted testers to experience the app as it would feel to use, rather than clicking only the hotspots we expected them to, so every control on screen does something. Where a real feature would need live data, other users or third-party services, we simulated it (Wizard of Oz) or used fixed data (hard-coded). This let us test the three task flows without building infrastructure that a medium-fidelity prototype doesn't call for.

### Wizard of Oz techniques

- **Mutual matching:** there are no other users. After **Find a match**, a "Checking your circle…" screen shows for about 1.5 seconds, then the prototype always "finds" a match with a friend from the circle you chose. The friend is picked by a fixed rule, not by anyone's real interest.
- **Calendar sync:** the switch doesn't connect to any calendar. The free window it shows (3:00–4:00pm) is fixed.
- **Add to Calendar:** shows a confirmation and marks the plan "Added," but nothing is written to a real calendar.
- **Directions:** "View Directions" and "Open directions" show a confirmation message instead of opening a maps app.
- **Forgot password:** shows "Reset link sent" without sending an email.
- **Share:** copies a sample invite message to the clipboard instead of opening a share sheet.
- **Free-time nudges:** the switch changes its state, but no notifications are sent.

### Hard-coded items

- **Login:** any valid-looking email and any password are accepted. Nothing is checked against real accounts or stored.
- **Free time and plan times:** "You have 1 hour free!", "Today · 3:00–4:00pm" (solo) and "Today, 3:30 PM" (meetup) are fixed. The status bar always shows 9:41 and 100%.
- **Places:** five fixed places (Matcha Café, Art Gallery, Bookstore, Mini Cat Town, Mini Golf Tour), with set walking times, price levels and photos. Mini Golf Tour is always the featured place on Discover.
- **Recommendations:** Home quick picks and Discover results don't depend on the interests you choose. Interests are saved for the session and shown in Profile, but they don't change any suggestions.
- **Maps:** the campus maps are a stylized drawing of our Figma map, not a real map. Place positions on it are fixed.
- **Visit history:** Profile starts with six example visits (Oct 3 to Oct 24) so the map isn't empty. Visits you confirm during testing are added to it.
- **Friends and contacts:** four starting friends (Tom, Jake, Sarah, Lynn) and four suggested contacts (Maya, Jess, Alex, Sophie). There is no contact sync. Starting circles are Close Friends (Jake, Lynn), Friends (Tom, Sarah) and Acquaintances (empty).
- **Budget:** default limits are $10 daily, $50 weekly and $200 monthly, each with example spending already logged. A confirmed visit adds a fixed cost: $8 for "$" places, $15 for "$$" and nothing for free places.
- **Session only:** nothing persists. Refreshing the page resets everything.

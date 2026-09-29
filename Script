/* =========================================
   ELEMENTS
========================================= */

const menuToggle =
  document.querySelector(".menu-toggle");

const siteNav =
  document.querySelector("#site-nav");

const navLinks =
  document.querySelectorAll(".site-nav a");

const sections =
  document.querySelectorAll("main section[id]");

const revealItems =
  document.querySelectorAll(".reveal");

const year =
  document.querySelector("#year");


/* =========================================
   COPYRIGHT YEAR
========================================= */

if (year) {

  year.textContent =
    new Date().getFullYear();

}


/* =========================================
   MOBILE NAVIGATION
========================================= */

const closeMenu = () => {

  if (!menuToggle || !siteNav) {
    return;
  }

  siteNav.classList.remove("open");

  menuToggle.setAttribute(
    "aria-expanded",
    "false"
  );

  const label =
    menuToggle.querySelector("span");

  if (label) {
    label.textContent = "Menu";
  }

};


if (menuToggle && siteNav) {

  menuToggle.addEventListener(
    "click",
    () => {

      const isOpen =
        siteNav.classList.toggle("open");

      menuToggle.setAttribute(
        "aria-expanded",
        String(isOpen)
      );

      const label =
        menuToggle.querySelector("span");

      if (label) {

        label.textContent =
          isOpen
            ? "Close"
            : "Menu";

      }

    }
  );


  navLinks.forEach((link) => {

    link.addEventListener(
      "click",
      () => {

        closeMenu();

      }
    );

  });

}


/* =========================================
   ESCAPE KEY
========================================= */

document.addEventListener(
  "keydown",
  (event) => {

    if (
      event.key === "Escape" &&
      siteNav?.classList.contains("open")
    ) {

      closeMenu();

      menuToggle?.focus();

    }

  }
);


/* =========================================
   ACTIVE NAVIGATION
========================================= */

const setActiveNav = () => {

  let current = "";

  sections.forEach((section) => {

    const top =
      section.getBoundingClientRect().top;

    if (top <= 140) {

      current =
        section.id;

    }

  });


  navLinks.forEach((link) => {

    const isActive =
      link.getAttribute("href") ===
      `#${current}`;

    link.classList.toggle(
      "active",
      isActive
    );

  });

};


window.addEventListener(
  "scroll",
  setActiveNav,
  {
    passive: true
  }
);


setActiveNav();


/* =========================================
   SCROLL REVEAL
========================================= */

if (
  "IntersectionObserver" in window
) {

  const observer =
    new IntersectionObserver(
      (entries, obs) => {

        entries.forEach(
          (entry) => {

            if (
              entry.isIntersecting
            ) {

              entry.target.classList.add(
                "visible"
              );

              obs.unobserve(
                entry.target
              );

            }

          }
        );

      },
      {
        threshold: 0.12
      }
    );


  revealItems.forEach(
    (item) => {

      observer.observe(item);

    }
  );

} else {

  revealItems.forEach(
    (item) => {

      item.classList.add(
        "visible"
      );

    }
  );

}

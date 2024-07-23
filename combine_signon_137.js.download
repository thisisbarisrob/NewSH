! function(b) {
    b(function() {
        var e = b.support,
            g;
        a: {
            g = document.createElement("bootstrap");
            var a = {
                    WebkitTransition: "webkitTransitionEnd",
                    MozTransition: "transitionend",
                    OTransition: "oTransitionEnd otransitionend",
                    transition: "transitionend"
                },
                c;
            for (c in a)
                if (void 0 !== g.style[c]) {
                    g = a[c];
                    break a
                }
            g = void 0
        }
        e.transition = g && {
            end: g
        }
    })
}(window.jQuery);
! function(b) {
    var e = function(a) {
        b(a).on("click", '[data-dismiss\x3d"alert"]', this.close)
    };
    e.prototype.close = function(a) {
        function c() {
            h.trigger("closed").remove()
        }
        var d = b(this),
            f = d.attr("data-target"),
            h;
        f || (f = (f = d.attr("href")) && f.replace(/.*(?=#[^\s]*$)/, ""));
        h = b(f);
        a && a.preventDefault();
        h.length || (h = d.hasClass("alert") ? d : d.parent());
        h.trigger(a = b.Event("close"));
        a.isDefaultPrevented() || (h.removeClass("in"), b.support.transition && h.hasClass("fade") ? h.on(b.support.transition.end, c) : c())
    };
    var g = b.fn.alert;
    b.fn.alert = function(a) {
        return this.each(function() {
            var c = b(this),
                d = c.data("alert");
            d || c.data("alert", d = new e(this));
            "string" == typeof a && d[a].call(c)
        })
    };
    b.fn.alert.Constructor = e;
    b.fn.alert.noConflict = function() {
        b.fn.alert = g;
        return this
    };
    b(document).on("click.alert.data-api", '[data-dismiss\x3d"alert"]', e.prototype.close)
}(window.jQuery);
! function(b) {
    var e = function(a, c) {
        this.$element = b(a);
        this.options = b.extend({}, b.fn.button.defaults, c)
    };
    e.prototype.setState = function(a) {
        var b = this.$element,
            d = b.data(),
            f = b.is("input") ? "val" : "html";
        a += "Text";
        d.resetText || b.data("resetText", b[f]());
        b[f](d[a] || this.options[a]);
        setTimeout(function() {
            "loadingText" == a ? b.addClass("disabled").attr("disabled", "disabled") : b.removeClass("disabled").removeAttr("disabled")
        }, 0)
    };
    e.prototype.toggle = function() {
        var a = this.$element.closest('[data-toggle\x3d"buttons-radio"]');
        a && a.find(".active").removeClass("active");
        this.$element.toggleClass("active")
    };
    var g = b.fn.button;
    b.fn.button = function(a) {
        return this.each(function() {
            var c = b(this),
                d = c.data("button"),
                f = "object" == typeof a && a;
            d || c.data("button", d = new e(this, f));
            "toggle" == a ? d.toggle() : a && d.setState(a)
        })
    };
    b.fn.button.defaults = {
        loadingText: "loading..."
    };
    b.fn.button.Constructor = e;
    b.fn.button.noConflict = function() {
        b.fn.button = g;
        return this
    };
    b(document).on("click.button.data-api", "[data-toggle^\x3dbutton]", function(a) {
        a =
            b(a.target);
        a.hasClass("btn") || (a = a.closest(".btn"));
        a.button("toggle")
    })
}(window.jQuery);
! function(b) {
    var e = function(a, c) {
        this.$element = b(a);
        this.$indicators = this.$element.find(".carousel-indicators");
        this.options = c;
        "hover" == this.options.pause && this.$element.on("mouseenter", b.proxy(this.pause, this)).on("mouseleave", b.proxy(this.cycle, this))
    };
    e.prototype = {
        cycle: function(a) {
            a || (this.paused = !1);
            this.interval && clearInterval(this.interval);
            this.options.interval && !this.paused && (this.interval = setInterval(b.proxy(this.next, this), this.options.interval));
            return this
        },
        getActiveIndex: function() {
            this.$active =
                this.$element.find(".item.active");
            this.$items = this.$active.parent().children();
            return this.$items.index(this.$active)
        },
        to: function(a) {
            var c = this.getActiveIndex(),
                d = this;
            if (!(a > this.$items.length - 1 || 0 > a)) return this.sliding ? this.$element.one("slid", function() {
                d.to(a)
            }) : c == a ? this.pause().cycle() : this.slide(a > c ? "next" : "prev", b(this.$items[a]))
        },
        pause: function(a) {
            a || (this.paused = !0);
            this.$element.find(".next, .prev").length && b.support.transition.end && (this.$element.trigger(b.support.transition.end),
                this.cycle(!0));
            clearInterval(this.interval);
            this.interval = null;
            return this
        },
        next: function() {
            if (!this.sliding) return this.slide("next")
        },
        prev: function() {
            if (!this.sliding) return this.slide("prev")
        },
        slide: function(a, c) {
            var d = this.$element.find(".item.active"),
                f = c || d[a](),
                h = this.interval,
                e = "next" == a ? "left" : "right",
                g = "next" == a ? "first" : "last",
                j = this;
            this.sliding = !0;
            h && this.pause();
            f = f.length ? f : this.$element.find(".item")[g]();
            g = b.Event("slide", {
                relatedTarget: f[0],
                direction: e
            });
            if (!f.hasClass("active")) {
                this.$indicators.length &&
                    (this.$indicators.find(".active").removeClass("active"), this.$element.one("slid", function() {
                        var a = b(j.$indicators.children()[j.getActiveIndex()]);
                        a && a.addClass("active")
                    }));
                if (b.support.transition && this.$element.hasClass("slide")) {
                    this.$element.trigger(g);
                    if (g.isDefaultPrevented()) return;
                    f.addClass(a);
                    f[0].offsetWidth;
                    d.addClass(e);
                    f.addClass(e);
                    this.$element.one(b.support.transition.end, function() {
                        f.removeClass([a, e].join(" ")).addClass("active");
                        d.removeClass(["active", e].join(" "));
                        j.sliding = !1;
                        setTimeout(function() {
                            j.$element.trigger("slid")
                        }, 0)
                    })
                } else {
                    this.$element.trigger(g);
                    if (g.isDefaultPrevented()) return;
                    d.removeClass("active");
                    f.addClass("active");
                    this.sliding = !1;
                    this.$element.trigger("slid")
                }
                h && this.cycle();
                return this
            }
        }
    };
    var g = b.fn.carousel;
    b.fn.carousel = function(a) {
        return this.each(function() {
            var c = b(this),
                d = c.data("carousel"),
                f = b.extend({}, b.fn.carousel.defaults, "object" == typeof a && a),
                h = "string" == typeof a ? a : f.slide;
            d || c.data("carousel", d = new e(this, f));
            if ("number" == typeof a) d.to(a);
            else if (h) d[h]();
            else f.interval && d.pause().cycle()
        })
    };
    b.fn.carousel.defaults = {
        interval: 5E3,
        pause: "hover"
    };
    b.fn.carousel.Constructor = e;
    b.fn.carousel.noConflict = function() {
        b.fn.carousel = g;
        return this
    };
    b(document).on("click.carousel.data-api", "[data-slide], [data-slide-to]", function(a) {
        var c = b(this),
            d, f = b(c.attr("data-target") || (d = c.attr("href")) && d.replace(/.*(?=#[^\s]+$)/, ""));
        d = b.extend({}, f.data(), c.data());
        var h;
        f.carousel(d);
        (h = c.attr("data-slide-to")) && f.data("carousel").pause().to(h).cycle();
        a.preventDefault()
    })
}(window.jQuery);
! function(b) {
    var e = function(a, c) {
        this.$element = b(a);
        this.options = b.extend({}, b.fn.collapse.defaults, c);
        this.options.parent && (this.$parent = b(this.options.parent));
        this.options.toggle && this.toggle()
    };
    e.prototype = {
        constructor: e,
        dimension: function() {
            return this.$element.hasClass("width") ? "width" : "height"
        },
        show: function() {
            var a, c, d, f;
            if (!this.transitioning && !this.$element.hasClass("in")) {
                a = this.dimension();
                c = b.camelCase(["scroll", a].join("-"));
                if ((d = this.$parent && this.$parent.find("\x3e .accordion-group \x3e .in")) && d.length) {
                    if ((f =
                            d.data("collapse")) && f.transitioning) return;
                    d.collapse("hide");
                    f || d.data("collapse", null)
                }
                this.$element[a](0);
                this.transition("addClass", b.Event("show"), "shown");
                b.support.transition && this.$element[a](this.$element[0][c])
            }
        },
        hide: function() {
            var a;
            !this.transitioning && this.$element.hasClass("in") && (a = this.dimension(), this.reset(this.$element[a]()), this.transition("removeClass", b.Event("hide"), "hidden"), this.$element[a](0))
        },
        reset: function(a) {
            var b = this.dimension();
            this.$element.removeClass("collapse")[b](a ||
                "auto")[0].offsetWidth;
            this.$element[null !== a ? "addClass" : "removeClass"]("collapse");
            return this
        },
        transition: function(a, c, d) {
            var f = this,
                h = function() {
                    "show" == c.type && f.reset();
                    f.transitioning = 0;
                    f.$element.trigger(d)
                };
            this.$element.trigger(c);
            c.isDefaultPrevented() || (this.transitioning = 1, this.$element[a]("in"), b.support.transition && this.$element.hasClass("collapse") ? this.$element.one(b.support.transition.end, h) : h())
        },
        toggle: function() {
            this[this.$element.hasClass("in") ? "hide" : "show"]()
        }
    };
    var g = b.fn.collapse;
    b.fn.collapse = function(a) {
        return this.each(function() {
            var c = b(this),
                d = c.data("collapse"),
                f = b.extend({}, b.fn.collapse.defaults, c.data(), "object" == typeof a && a);
            d || c.data("collapse", d = new e(this, f));
            if ("string" == typeof a) d[a]()
        })
    };
    b.fn.collapse.defaults = {
        toggle: !0
    };
    b.fn.collapse.Constructor = e;
    b.fn.collapse.noConflict = function() {
        b.fn.collapse = g;
        return this
    };
    b(document).on("click.collapse.data-api", "[data-toggle\x3dcollapse]", function(a) {
        var c = b(this),
            d;
        a = c.attr("data-target") || a.preventDefault() || (d =
            c.attr("href")) && d.replace(/.*(?=#[^\s]+$)/, "");
        d = b(a).data("collapse") ? "toggle" : c.data();
        c[b(a).hasClass("in") ? "addClass" : "removeClass"]("collapsed");
        b(a).collapse(d)
    })
}(window.jQuery);
! function(b) {
    function e() {
        b(a).each(function() {
            g(b(this)).removeClass("open")
        })
    }

    function g(a) {
        var c = a.attr("data-target");
        c || (c = (c = a.attr("href")) && /#/.test(c) && c.replace(/.*(?=#[^\s]*$)/, ""));
        c = c && b(c);
        if (!c || !c.length) c = a.parent();
        return c
    }
    var a = "[data-toggle\x3ddropdown]",
        c = function(a) {
            var c = b(a).on("click.dropdown.data-api", this.toggle);
            b("html").on("click.dropdown.data-api", function() {
                c.parent().removeClass("open")
            })
        };
    c.prototype = {
        constructor: c,
        toggle: function() {
            var a = b(this),
                c, d;
            if (!a.is(".disabled, :disabled")) return c =
                g(a), d = c.hasClass("open"), e(), d || c.toggleClass("open"), a.trigger( "focus" ), !1
        },
        keydown: function(c) {
            var d, e, i;
            if (/(38|40|27)/.test(c.keyCode) && (d = b(this), c.preventDefault(), c.stopPropagation(), !d.is(".disabled, :disabled"))) {
                e = g(d);
                i = e.hasClass("open");
                if (!i || i && 27 == c.keyCode) return 27 == c.which && e.find(a).trigger( "focus" ), d.click();
                d = b("[role\x3dmenu] li:not(.divider):visible a", e);
                d.length && (e = d.index(d.filter(":focus")), 38 == c.keyCode && 0 < e && e--, 40 == c.keyCode && e < d.length - 1 && e++, ~e || (e = 0), d.eq(e).trigger("focus"))
            }
        }
    };
    var d = b.fn.dropdown;
    b.fn.dropdown = function(a) {
        return this.each(function() {
            var d = b(this),
                e = d.data("dropdown");
            e || d.data("dropdown", e = new c(this));
            "string" == typeof a && e[a].call(d)
        })
    };
    b.fn.dropdown.Constructor = c;
    b.fn.dropdown.noConflict = function() {
        b.fn.dropdown = d;
        return this
    };
    b(document).on("click.dropdown.data-api", e).on("click.dropdown.data-api", ".dropdown form", function(a) {
        a.stopPropagation()
    }).on("click.dropdown-menu", function(a) {
        a.stopPropagation()
    }).on("click.dropdown.data-api", a, c.prototype.toggle).on("keydown.dropdown.data-api",
        a + ", [role\x3dmenu]", c.prototype.keydown)
}(window.jQuery);
! function(b) {
    var e = function(a, c) {
        this.options = c;
        // $(elements).delegate(selector, events, data, handler); (deprecated)
        // this.$element = b(a).delegate('[data-dismiss\x3d"modal"]', "click.dismiss.modal", b.proxy(this.hide, this));
        // $(elements).on(events, selector, data, handler); (new way)
        this.$element = b(a).on("click.dismiss.modal", '[data-dismiss\x3d"modal"]', b.proxy(this.hide, this));
        this.options.remote && this.$element.find(".modal-body").load(this.options.remote)
    };
    e.prototype = {
        constructor: e,
        toggle: function() {
            return this[!this.isShown ? "show" : "hide"]()
        },
        show: function() {
            var a = this,
                c = b.Event("show");
            this.$element.trigger(c);
            !this.isShown && !c.isDefaultPrevented() && (this.isShown = !0, this.escape(), this.backdrop(function() {
                var c = b.support.transition &&
                    a.$element.hasClass("fade");
                a.$element.parent().length || a.$element.appendTo(document.body);
                a.$element.show();
                c && a.$element[0].offsetWidth;
                a.$element.addClass("in").attr("aria-hidden", !1);
                a.enforceFocus();
                c ? a.$element.one(b.support.transition.end, function() {
                    a.$element.trigger("focus").trigger("shown")
                }) : a.$element.trigger("focus").trigger("shown")
            }))
        },
        hide: function(a) {
            a && a.preventDefault();
            a = b.Event("hide");
            this.$element.trigger(a);
            this.isShown && !a.isDefaultPrevented() && (this.isShown = !1, this.escape(), b(document).off("focusin.modal"),
                this.$element.removeClass("in").attr("aria-hidden", !0), b.support.transition && this.$element.hasClass("fade") ? this.hideWithTransition() : this.hideModal())
        },
        enforceFocus: function() {
            var a = this;
            b(document).on("focusin.modal", function(b) {
                a.$element[0] !== b.target && !a.$element.has(b.target).length && a.$element.trigger("focus")
            })
        },
        escape: function() {
            var a = this;
            if (this.isShown && this.options.keyboard) this.$element.on("keyup.dismiss.modal", function(b) {
                27 == b.which && a.hide()
            });
            else this.isShown || this.$element.off("keyup.dismiss.modal")
        },
        hideWithTransition: function() {
            var a = this,
                c = setTimeout(function() {
                    a.$element.off(b.support.transition.end);
                    a.hideModal()
                }, 500);
            this.$element.one(b.support.transition.end, function() {
                clearTimeout(c);
                a.hideModal()
            })
        },
        hideModal: function() {
            var a = this;
            this.$element.hide();
            this.backdrop(function() {
                a.removeBackdrop();
                a.$element.trigger("hidden")
            })
        },
        removeBackdrop: function() {
            this.$backdrop && this.$backdrop.remove();
            this.$backdrop = null
        },
        backdrop: function(a) {
            var c = this.$element.hasClass("fade") ? "fade" : "";
            if (this.isShown &&
                this.options.backdrop) {
                var d = b.support.transition && c;
                this.$backdrop = b('\x3cdiv id="modal-backdrop" class\x3d"modal-backdrop ' + c + '" /\x3e').appendTo(document.body);
                this.$backdrop.on("click", "static" == this.options.backdrop ? b.proxy(this.$element[0].focus, this.$element[0]) : b.proxy(this.hide, this));
                d && this.$backdrop[0].offsetWidth;
                this.$backdrop.addClass("in");
                a && (d ? this.$backdrop.one(b.support.transition.end, a) : a())
            } else !this.isShown && this.$backdrop ? (this.$backdrop.removeClass("in"), b.support.transition && this.$element.hasClass("fade") ?
                this.$backdrop.one(b.support.transition.end, a) : a()) : a && a()
        }
    };
    var g = b.fn.modal;
    b.fn.modal = function(a) {
        return this.each(function() {
            var c = b(this),
                d = c.data("modal"),
                f = b.extend({}, b.fn.modal.defaults, c.data(), "object" == typeof a && a);
            d || c.data("modal", d = new e(this, f));
            if ("string" == typeof a) d[a]();
            else f.show && d.show()
        })
    };
    b.fn.modal.defaults = {
        backdrop: !0,
        keyboard: !0,
        show: !0
    };
    b.fn.modal.Constructor = e;
    b.fn.modal.noConflict = function() {
        b.fn.modal = g;
        return this
    };
    b(document).on("click.modal.data-api", '[data-toggle\x3d"modal"]',
        function(a) {
            var c = b(this),
                d = c.attr("href"),
                f = b(c.attr("data-target") || d && d.replace(/.*(?=#[^\s]+$)/, "")),
                d = f.data("modal") ? "toggle" : b.extend({
                    remote: !/#/.test(d) && d
                }, f.data(), c.data());
            a.preventDefault();
            f.modal(d).one("hide", function() {
                c.trigger("focus")
            })
        })
}(window.jQuery);
! function(b) {
    var e = function(a, b) {
        this.init("tooltip", a, b)
    };
    e.prototype = {
        constructor: e,
        init: function(a, c, d) {
            var f;
            this.type = a;
            this.$element = b(c);
            this.options = this.getOptions(d);
            this.enabled = !0;
            c = this.options.trigger.split(" ");
            for (d = c.length; d--;)
                if (f = c[d], "click" == f) this.$element.on("click." + this.type, this.options.selector, b.proxy(this.toggle, this));
                else "manual" != f && (a = "hover" == f ? "mouseenter" : "focus", f = "hover" == f ? "mouseleave" : "blur", this.$element.on(a + "." + this.type, this.options.selector, b.proxy(this.enter,
                    this)), this.$element.on(f + "." + this.type, this.options.selector, b.proxy(this.leave, this)));
            this.options.selector ? this._options = b.extend({}, this.options, {
                trigger: "manual",
                selector: ""
            }) : this.fixTitle()
        },
        getOptions: function(a) {
            a = b.extend({}, b.fn[this.type].defaults, this.$element.data(), a);
            a.delay && "number" == typeof a.delay && (a.delay = {
                show: a.delay,
                hide: a.delay
            });
            return a
        },
        enter: function(a) {
            var c = b.fn[this.type].defaults,
                d = {},
                f;
            this._options && b.each(this._options, function(a, b) {
                c[a] != b && (d[a] = b)
            }, this);
            f =
                b(a.currentTarget)[this.type](d).data(this.type);
            if (!f.options.delay || !f.options.delay.show) return f.show();
            clearTimeout(this.timeout);
            f.hoverState = "in";
            this.timeout = setTimeout(function() {
                "in" == f.hoverState && f.show()
            }, f.options.delay.show)
        },
        leave: function(a) {
            var c = b(a.currentTarget)[this.type](this._options).data(this.type);
            this.timeout && clearTimeout(this.timeout);
            if (!c.options.delay || !c.options.delay.hide) return c.hide();
            c.hoverState = "out";
            this.timeout = setTimeout(function() {
                "out" == c.hoverState &&
                    c.hide()
            }, c.options.delay.hide)
        },
        show: function() {
            var a, c, d, f, e;
            c = b.Event("show");
            if (this.hasContent() && this.enabled && (this.$element.trigger(c), !c.isDefaultPrevented())) {
                a = this.tip();
                this.setContent();
                this.options.animation && a.addClass("fade");
                f = "function" == typeof this.options.placement ? this.options.placement.call(this, a[0], this.$element[0]) : this.options.placement;
                a.detach().css({
                    top: 0,
                    left: 0,
                    display: "block"
                });
                this.options.container ? a.appendTo(this.options.container) : a.insertAfter(this.$element);
                c =
                    this.getPosition();
                d = a[0].offsetWidth;
                a = a[0].offsetHeight;
                switch (f) {
                    case "bottom":
                        e = {
                            top: c.top + c.height,
                            left: c.left + c.width / 2 - d / 2
                        };
                        break;
                    case "top":
                        e = {
                            top: c.top - a,
                            left: c.left + c.width / 2 - d / 2
                        };
                        break;
                    case "left":
                        e = {
                            top: c.top + c.height / 2 - a / 2,
                            left: c.left - d
                        };
                        break;
                    case "right":
                        e = {
                            top: c.top + c.height / 2 - a / 2,
                            left: c.left + c.width
                        }
                }
                this.applyPlacement(e, f);
                this.$element.trigger("shown")
            }
        },
        applyPlacement: function(a, b) {
            var d = this.tip(),
                f = d[0].offsetWidth,
                e = d[0].offsetHeight,
                g, i, j;
            d.offset(a).addClass(b).addClass("in");
            g = d[0].offsetWidth;
            i = d[0].offsetHeight;
            "top" == b && i != e && (a.top = a.top + e - i, j = !0);
            "bottom" == b || "top" == b ? (e = 0, 0 > a.left && (e = -2 * a.left, a.left = 0, d.offset(a), g = d[0].offsetWidth), this.replaceArrow(e - f + g, g, "left")) : this.replaceArrow(i - e, i, "top");
            j && d.offset(a)
        },
        replaceArrow: function(a, b, d) {
            this.arrow().css(d, a ? 50 * (1 - a / b) + "%" : "")
        },
        setContent: function() {
            var a = this.tip(),
                b = this.getTitle();
            a.find(".tooltip-inner")[this.options.html ? "html" : "text"](b);
            a.removeClass("fade in top bottom left right")
        },
        hide: function() {
            var a =
                this.tip(),
                c = b.Event("hide");
            this.$element.trigger(c);
            if (!c.isDefaultPrevented()) {
                a.removeClass("in");
                if (b.support.transition && this.$tip.hasClass("fade")) {
                    var d = setTimeout(function() {
                        a.off(b.support.transition.end).detach()
                    }, 500);
                    a.one(b.support.transition.end, function() {
                        clearTimeout(d);
                        a.detach()
                    })
                } else a.detach();
                this.$element.trigger("hidden");
                return this
            }
        },
        fixTitle: function() {
            var a = this.$element;
            if (a.attr("title") || "string" != typeof a.attr("data-original-title")) a.attr("data-original-title", a.attr("title") ||
                "").attr("title", "")
        },
        hasContent: function() {
            return this.getTitle()
        },
        getPosition: function() {
            var a = this.$element[0];
            return b.extend({}, "function" == typeof a.getBoundingClientRect ? a.getBoundingClientRect() : {
                width: a.offsetWidth,
                height: a.offsetHeight
            }, this.$element.offset())
        },
        getTitle: function() {
            var a = this.$element,
                b = this.options;
            return a.attr("data-original-title") || ("function" == typeof b.title ? b.title.call(a[0]) : b.title)
        },
        tip: function() {
            return this.$tip = this.$tip || b(this.options.template)
        },
        arrow: function() {
            return this.$arrow =
                this.$arrow || this.tip().find(".tooltip-arrow")
        },
        validate: function() {
            this.$element[0].parentNode || (this.hide(), this.options = this.$element = null)
        },
        enable: function() {
            this.enabled = !0
        },
        disable: function() {
            this.enabled = !1
        },
        toggleEnabled: function() {
            this.enabled = !this.enabled
        },
        toggle: function(a) {
            a = a ? b(a.currentTarget)[this.type](this._options).data(this.type) : this;
            a.tip().hasClass("in") ? a.hide() : a.show()
        },
        destroy: function() {
            this.hide().$element.off("." + this.type).removeData(this.type)
        }
    };
    var g = b.fn.tooltip;
    b.fn.tooltip = function(a) {
        return this.each(function() {
            var c = b(this),
                d = c.data("tooltip"),
                f = "object" == typeof a && a;
            d || c.data("tooltip", d = new e(this, f));
            if ("string" == typeof a) d[a]()
        })
    };
    b.fn.tooltip.Constructor = e;
    b.fn.tooltip.defaults = {
        animation: !0,
        placement: "top",
        selector: !1,
        template: '\x3cdiv class\x3d"tooltip"\x3e\x3cdiv class\x3d"tooltip-arrow"\x3e\x3c/div\x3e\x3cdiv class\x3d"tooltip-inner"\x3e\x3c/div\x3e\x3c/div\x3e',
        trigger: "hover focus",
        title: "",
        delay: 0,
        html: !1,
        container: !1
    };
    b.fn.tooltip.noConflict =
        function() {
            b.fn.tooltip = g;
            return this
        }
}(window.jQuery);
! function(b) {
    var e = function(a, b) {
        this.init("popover", a, b)
    };
    e.prototype = b.extend({}, b.fn.tooltip.Constructor.prototype, {
        constructor: e,
        setContent: function() {
            var a = this.tip(),
                b = this.getTitle(),
                d = this.getContent();
            a.find(".popover-title")[this.options.html ? "html" : "text"](b);
            a.find(".popover-content")[this.options.html ? "html" : "text"](d);
            a.removeClass("fade top bottom left right in")
        },
        hasContent: function() {
            return this.getTitle() || this.getContent()
        },
        getContent: function() {
            var a = this.$element,
                b = this.options;
            return ("function" == typeof b.content ? b.content.call(a[0]) : b.content) || a.attr("data-content")
        },
        tip: function() {
            this.$tip || (this.$tip = b(this.options.template));
            return this.$tip
        },
        destroy: function() {
            this.hide().$element.off("." + this.type).removeData(this.type)
        }
    });
    var g = b.fn.popover;
    b.fn.popover = function(a) {
        return this.each(function() {
            var c = b(this),
                d = c.data("popover"),
                f = "object" == typeof a && a;
            d || c.data("popover", d = new e(this, f));
            if ("string" == typeof a) d[a]()
        })
    };
    b.fn.popover.Constructor = e;
    b.fn.popover.defaults =
        b.extend({}, b.fn.tooltip.defaults, {
            placement: "right",
            trigger: "click",
            content: "",
            template: '\x3cdiv class\x3d"popover"\x3e\x3cdiv class\x3d"arrow"\x3e\x3c/div\x3e\x3ch3 class\x3d"popover-title"\x3e\x3c/h3\x3e\x3cdiv class\x3d"popover-content"\x3e\x3c/div\x3e\x3c/div\x3e'
        });
    b.fn.popover.noConflict = function() {
        b.fn.popover = g;
        return this
    }
}(window.jQuery);
! function(b) {
    function e(a, c) {
        var d = b.proxy(this.process, this),
            f = b(a).is("body") ? b(window) : b(a),
            e;
        this.options = b.extend({}, b.fn.scrollspy.defaults, c);
        this.$scrollElement = f.on("scroll.scroll-spy.data-api", d);
        this.selector = (this.options.target || (e = b(a).attr("href")) && e.replace(/.*(?=#[^\s]+$)/, "") || "") + " .nav li \x3e a";
        this.$body = b("body");
        this.refresh();
        this.process()
    }
    e.prototype = {
        constructor: e,
        refresh: function() {
            var a = this;
            this.offsets = b([]);
            this.targets = b([]);
            this.$body.find(this.selector).map(function() {
                var c =
                    b(this),
                    c = c.data("target") || c.attr("href"),
                    d = /^#\w/.test(c) && b(c);
                return d && d.length && [
                    [d.position().top + (!b.isWindow(a.$scrollElement.get(0)) && a.$scrollElement.scrollTop()), c]
                ] || null
            }).sort(function(a, b) {
                return a[0] - b[0]
            }).each(function() {
                a.offsets.push(this[0]);
                a.targets.push(this[1])
            })
        },
        process: function() {
            var a = this.$scrollElement.scrollTop() + this.options.offset,
                b = (this.$scrollElement[0].scrollHeight || this.$body[0].scrollHeight) - this.$scrollElement.height(),
                d = this.offsets,
                f = this.targets,
                e = this.activeTarget,
                g;
            if (a >= b) return e != (g = f.last()[0]) && this.activate(g);
            for (g = d.length; g--;) e != f[g] && a >= d[g] && (!d[g + 1] || a <= d[g + 1]) && this.activate(f[g])
        },
        activate: function(a) {
            this.activeTarget = a;
            b(this.selector).parent(".active").removeClass("active");
            a = b(this.selector + '[data-target\x3d"' + a + '"],' + this.selector + '[href\x3d"' + a + '"]').parent("li").addClass("active");
            a.parent(".dropdown-menu").length && (a = a.closest("li.dropdown").addClass("active"));
            a.trigger("activate")
        }
    };
    var g = b.fn.scrollspy;
    b.fn.scrollspy = function(a) {
        return this.each(function() {
            var c =
                b(this),
                d = c.data("scrollspy"),
                f = "object" == typeof a && a;
            d || c.data("scrollspy", d = new e(this, f));
            if ("string" == typeof a) d[a]()
        })
    };
    b.fn.scrollspy.Constructor = e;
    b.fn.scrollspy.defaults = {
        offset: 10
    };
    b.fn.scrollspy.noConflict = function() {
        b.fn.scrollspy = g;
        return this
    };
    b(window).on("load", function() {
        b('[data-spy\x3d"scroll"]').each(function() {
            var a = b(this);
            a.scrollspy(a.data())
        })
    })
}(window.jQuery);
! function(b) {
    var e = function(a) {
        this.element = b(a)
    };
    e.prototype = {
        constructor: e,
        show: function() {
            var a = this.element,
                c = a.closest("ul:not(.dropdown-menu)"),
                d = a.attr("data-target"),
                f, e;
            d || (d = (d = a.attr("href")) && d.replace(/.*(?=#[^\s]*$)/, ""));
            a.parent("li").hasClass("active") || (f = c.find(".active:last a")[0], e = b.Event("show", {
                relatedTarget: f
            }), a.trigger(e), e.isDefaultPrevented() || (d = b(d), this.activate(a.parent("li"), c), this.activate(d, d.parent(), function() {
                a.trigger({
                    type: "shown",
                    relatedTarget: f
                })
            })))
        },
        activate: function(a,
            c, d) {
            function f() {
                e.removeClass("active").find("\x3e .dropdown-menu \x3e .active").removeClass("active");
                a.addClass("active");
                g ? (a[0].offsetWidth, a.addClass("in")) : a.removeClass("fade");
                a.parent(".dropdown-menu") && a.closest("li.dropdown").addClass("active");
                d && d()
            }
            var e = c.find("\x3e .active"),
                g = d && b.support.transition && e.hasClass("fade");
            g ? e.one(b.support.transition.end, f) : f();
            e.removeClass("in")
        }
    };
    var g = b.fn.tab;
    b.fn.tab = function(a) {
        return this.each(function() {
            var c = b(this),
                d = c.data("tab");
            d || c.data("tab",
                d = new e(this));
            if ("string" == typeof a) d[a]()
        })
    };
    b.fn.tab.Constructor = e;
    b.fn.tab.noConflict = function() {
        b.fn.tab = g;
        return this
    };
    b(document).on("click.tab.data-api", '[data-toggle\x3d"tab"], [data-toggle\x3d"pill"]', function(a) {
        a.preventDefault();
        b(this).tab("show")
    })
}(window.jQuery);
! function(b) {
    var e = function(a, c) {
        this.$element = b(a);
        this.options = b.extend({}, b.fn.typeahead.defaults, c);
        this.matcher = this.options.matcher || this.matcher;
        this.sorter = this.options.sorter || this.sorter;
        this.highlighter = this.options.highlighter || this.highlighter;
        this.updater = this.options.updater || this.updater;
        this.source = this.options.source;
        this.$menu = b(this.options.menu);
        this.shown = !1;
        this.listen()
    };
    e.prototype = {
        constructor: e,
        select: function() {
            var a = this.$menu.find(".active").attr("data-value");
            this.$element.val(this.updater(a)).change();
            return this.hide()
        },
        updater: function(a) {
            return a
        },
        show: function() {
            var a = b.extend({}, this.$element.position(), {
                height: this.$element[0].offsetHeight
            });
            this.$menu.insertAfter(this.$element).css({
                top: a.top + a.height,
                left: a.left
            }).show();
            this.shown = !0;
            return this
        },
        hide: function() {
            this.$menu.hide();
            this.shown = !1;
            return this
        },
        lookup: function() {
            var a;
            this.query = this.$element.val();
            return !this.query || this.query.length < this.options.minLength ? this.shown ? this.hide() : this : (a = b.isFunction(this.source) ? this.source(this.query,
                b.proxy(this.process, this)) : this.source) ? this.process(a) : this
        },
        process: function(a) {
            var c = this;
            a = b.grep(a, function(a) {
                return c.matcher(a)
            });
            a = this.sorter(a);
            return !a.length ? this.shown ? this.hide() : this : this.render(a.slice(0, this.options.items)).show()
        },
        matcher: function(a) {
            return ~a.toLowerCase().indexOf(this.query.toLowerCase())
        },
        sorter: function(a) {
            for (var b = [], d = [], e = [], g; g = a.shift();) g.toLowerCase().indexOf(this.query.toLowerCase()) ? ~g.indexOf(this.query) ? d.push(g) : e.push(g) : b.push(g);
            return b.concat(d,
                e)
        },
        highlighter: function(a) {
            var b = this.query.replace(/[\-\[\]{}()*+?.,\\\^$|#\s]/g, "\\$\x26");
            return a.replace(RegExp("(" + b + ")", "ig"), function(a, b) {
                return "\x3cstrong\x3e" + b + "\x3c/strong\x3e"
            })
        },
        render: function(a) {
            var c = this;
            a = b(a).map(function(a, e) {
                a = b(c.options.item).attr("data-value", e);
                a.find("a").html(c.highlighter(e));
                return a[0]
            });
            a.first().addClass("active");
            this.$menu.html(a);
            return this
        },
        next: function() {
            var a = this.$menu.find(".active").removeClass("active").next();
            a.length || (a = b(this.$menu.find("li")[0]));
            a.addClass("active")
        },
        prev: function() {
            var a = this.$menu.find(".active").removeClass("active").prev();
            a.length || (a = this.$menu.find("li").last());
            a.addClass("active")
        },
        listen: function() {
            this.$element.on("focus", b.proxy(this.focus, this)).on("blur", b.proxy(this.blur, this)).on("keypress", b.proxy(this.keypress, this)).on("keyup", b.proxy(this.keyup, this));
            if (this.eventSupported("keydown")) this.$element.on("keydown", b.proxy(this.keydown, this));
            this.$menu.on("click", b.proxy(this.click, this)).on("mouseenter",
                "li", b.proxy(this.mouseenter, this)).on("mouseleave", "li", b.proxy(this.mouseleave, this))
        },
        eventSupported: function(a) {
            var b = a in this.$element;
            b || (this.$element.setAttribute(a, "return;"), b = "function" === typeof this.$element[a]);
            return b
        },
        move: function(a) {
            if (this.shown) {
                switch (a.keyCode) {
                    case 9:
                    case 13:
                    case 27:
                        a.preventDefault();
                        break;
                    case 38:
                        a.preventDefault();
                        this.prev();
                        break;
                    case 40:
                        a.preventDefault(), this.next()
                }
                a.stopPropagation()
            }
        },
        keydown: function(a) {
            this.suppressKeyPressRepeat = ~b.inArray(a.keyCode, [40, 38, 9, 13, 27]);
            this.move(a)
        },
        keypress: function(a) {
            this.suppressKeyPressRepeat || this.move(a)
        },
        keyup: function(a) {
            switch (a.keyCode) {
                case 40:
                case 38:
                case 16:
                case 17:
                case 18:
                    break;
                case 9:
                case 13:
                    if (!this.shown) return;
                    this.select();
                    break;
                case 27:
                    if (!this.shown) return;
                    this.hide();
                    break;
                default:
                    this.lookup()
            }
            a.stopPropagation();
            a.preventDefault()
        },
        focus: function() {
            this.focused = !0
        },
        blur: function() {
            this.focused = !1;
            !this.mousedover && this.shown && this.hide()
        },
        click: function(a) {
            a.stopPropagation();
            a.preventDefault();
            this.select();
            this.$element.trigger("focus")
        },
        mouseenter: function(a) {
            this.mousedover = !0;
            this.$menu.find(".active").removeClass("active");
            b(a.currentTarget).addClass("active")
        },
        mouseleave: function() {
            this.mousedover = !1;
            !this.focused && this.shown && this.hide()
        }
    };
    var g = b.fn.typeahead;
    b.fn.typeahead = function(a) {
        return this.each(function() {
            var c = b(this),
                d = c.data("typeahead"),
                f = "object" == typeof a && a;
            d || c.data("typeahead", d = new e(this, f));
            if ("string" == typeof a) d[a]()
        })
    };
    b.fn.typeahead.defaults = {
        source: [],
        items: 8,
        menu: '\x3cul class\x3d"typeahead dropdown-menu"\x3e\x3c/ul\x3e',
        item: '\x3cli\x3e\x3ca href\x3d"#"\x3e\x3c/a\x3e\x3c/li\x3e',
        minLength: 1
    };
    b.fn.typeahead.Constructor = e;
    b.fn.typeahead.noConflict = function() {
        b.fn.typeahead = g;
        return this
    };
    b(document).on("focus.typeahead.data-api", '[data-provide\x3d"typeahead"]', function() {
        var a = b(this);
        a.data("typeahead") || a.typeahead(a.data())
    })
}(window.jQuery);
! function(b) {
    var e = function(a, c) {
        this.options = b.extend({}, b.fn.affix.defaults, c);
        this.$window = b(window).on("scroll.affix.data-api", b.proxy(this.checkPosition, this)).on("click.affix.data-api", b.proxy(function() {
            setTimeout(b.proxy(this.checkPosition, this), 1)
        }, this));
        this.$element = b(a);
        this.checkPosition()
    };
    e.prototype.checkPosition = function() {
        if (this.$element.is(":visible")) {
            var a = b(document).height(),
                c = this.$window.scrollTop(),
                d = this.$element.offset(),
                e = this.options.offset,
                g = e.bottom,
                k = e.top;
            "object" !=
            typeof e && (g = k = e);
            "function" == typeof k && (k = e.top());
            "function" == typeof g && (g = e.bottom());
            a = null != this.unpin && c + this.unpin <= d.top ? !1 : null != g && d.top + this.$element.height() >= a - g ? "bottom" : null != k && c <= k ? "top" : !1;
            this.affixed !== a && (this.affixed = a, this.unpin = "bottom" == a ? d.top - c : null, this.$element.removeClass("affix affix-top affix-bottom").addClass("affix" + (a ? "-" + a : "")))
        }
    };
    var g = b.fn.affix;
    b.fn.affix = function(a) {
        return this.each(function() {
            var c = b(this),
                d = c.data("affix"),
                f = "object" == typeof a && a;
            d || c.data("affix",
                d = new e(this, f));
            if ("string" == typeof a) d[a]()
        })
    };
    b.fn.affix.Constructor = e;
    b.fn.affix.defaults = {
        offset: 0
    };
    b.fn.affix.noConflict = function() {
        b.fn.affix = g;
        return this
    };
    b(window).on("load", function() {
        b('[data-spy\x3d"affix"]').each(function() {
            var a = b(this),
                c = a.data();
            c.offset = c.offset || {};
            c.offsetBottom && (c.offset.bottom = c.offsetBottom);
            c.offsetTop && (c.offset.top = c.offsetTop);
            a.affix(c)
        })
    })
}(window.jQuery);
window.Modernizr = function(l, e, B) {
    function C(a, c) {
        for (var f in a) {
            var q = a[f];
            if (!~("" + q).indexOf("-") && z[q] !== B) return "pfx" == c ? q : !0
        }
        return !1
    }

    function m(a, c, f) {
        var q = a.charAt(0).toUpperCase() + a.slice(1),
            b = (a + " " + u.join(q + " ") + q).split(" ");
        if ("string" === typeof c || "undefined" === typeof c) c = C(b, c);
        else {
            b = (a + " " + A.join(q + " ") + q).split(" ");
            a: {
                a = b;
                for (var d in a)
                    if (q = c[a[d]], q !== B) {
                        c = !1 === f ? a[d] : "function" === typeof q ? q.bind(f || c) : q;
                        break a
                    }
                c = !1
            }
        }
        return c
    }
    var g = {},
        s = e.documentElement,
        d = e.createElement("modernizr"),
        z = d.style,
        D = " -webkit- -moz- -o- -ms- ".split(" "),
        u = ["Webkit", "Moz", "O", "ms"],
        A = ["webkit", "moz", "o", "ms"],
        d = {},
        v = [],
        E = v.slice,
        t, w = function(a, c, f, b) {
            var d, k, i, p, h = e.createElement("div"),
                y = e.body,
                g = y || e.createElement("body");
            if (parseInt(f, 10))
                for (; f--;) i = e.createElement("div"), i.id = b ? b[f] : "modernizr" + (f + 1), h.appendChild(i);
            return d = ['\x26#173;\x3cstyle id\x3d"smodernizr"\x3e', a, "\x3c/style\x3e"].join(""), h.id = "modernizr", (y ? h : g).innerHTML += d, g.appendChild(h), y || (g.style.background = "", g.style.overflow =
                "hidden", p = s.style.overflow, s.style.overflow = "hidden", s.appendChild(g)), k = c(h, a), y ? h.parentNode.removeChild(h) : (g.parentNode.removeChild(g), s.style.overflow = p), !!k
        },
        H, K = {
            select: "input",
            change: "input",
            submit: "form",
            reset: "form",
            error: "img",
            load: "img",
            abort: "img"
        };
    H = function(a, c) {
        c = c || e.createElement(K[a] || "div");
        a = "on" + a;
        var f = a in c;
        return f || (c.setAttribute || (c = e.createElement("div")), c.setAttribute && c.removeAttribute && (c.setAttribute(a, ""), f = "function" === typeof c[a], "undefined" === typeof c[a] || (c[a] =
            B), c.removeAttribute(a))), f
    };
    var I = {}.hasOwnProperty,
        F;
    "undefined" !== typeof I && "undefined" !== typeof I.call ? F = function(a, c) {
        return I.call(a, c)
    } : F = function(a, c) {
        return c in a && "undefined" === typeof a.constructor.prototype[c]
    };
    Function.prototype.bind || (Function.prototype.bind = function(a) {
        var c = this;
        if ("function" != typeof c) throw new TypeError;
        var f = E.call(arguments, 1),
            b = function() {
                if (this instanceof b) {
                    var d = function() {};
                    d.prototype = c.prototype;
                    var d = new d,
                        e = c.apply(d, f.concat(E.call(arguments)));
                    return Object(e) ===
                        e ? e : d
                }
                return c.apply(a, f.concat(E.call(arguments)))
            };
        return b
    });
    d.flexbox = function() {
        return m("flexWrap")
    };
    d.flexboxlegacy = function() {
        return m("boxDirection")
    };
    d.touch = function() {
        var a;
        return "ontouchstart" in l || l.DocumentTouch && e instanceof DocumentTouch ? a = !0 : w(["@media (", D.join("touch-enabled),("), "modernizr){#modernizr{top:9px;position:absolute}}"].join(""), function(c) {
            a = 9 === c.offsetTop
        }), a
    };
    d.geolocation = function() {
        return "geolocation" in navigator
    };
    d.postmessage = function() {
        return !!l.postMessage
    };
    d.hashchange = function() {
        return H("hashchange", l) && (e.documentMode === B || 7 < e.documentMode)
    };
    d.history = function() {
        return !!l.history && !!history.pushState
    };
    d.draganddrop = function() {
        var a = e.createElement("div");
        return "draggable" in a || "ondragstart" in a && "ondrop" in a
    };
    d.backgroundsize = function() {
        return m("backgroundSize")
    };
    d.borderimage = function() {
        return m("borderImage")
    };
    d.borderradius = function() {
        return m("borderRadius")
    };
    d.boxshadow = function() {
        return m("boxShadow")
    };
    d.textshadow = function() {
        return "" === e.createElement("div").style.textShadow
    };
    d.opacity = function() {
        var a = D.join("opacity:.55;") + "";
        z.cssText = a;
        return /^0.55$/.test(z.opacity)
    };
    d.cssanimations = function() {
        return m("animationName")
    };
    d.csscolumns = function() {
        return m("columnCount")
    };
    d.cssgradients = function() {
        var a = ("background-image:-webkit-gradient(linear,left top,right bottom,from(#9f9),to(white));background-image:" + D.join("linear-gradient(left top,#9f9, white);background-image:")).slice(0, -17);
        z.cssText = a;
        return !!~("" + z.backgroundImage).indexOf("gradient")
    };
    d.cssreflections = function() {
        return m("boxReflect")
    };
    d.csstransforms = function() {
        return !!m("transform")
    };
    d.csstransforms3d = function() {
        var a = !!m("perspective");
        return a && "webkitPerspective" in s.style && w("@media (transform-3d),(-webkit-transform-3d){#modernizr{left:9px;position:absolute;height:3px;}}", function(c) {
            a = 9 === c.offsetLeft && 3 === c.offsetHeight
        }), a
    };
    d.csstransitions = function() {
        return m("transition")
    };
    d.fontface = function() {
        var a;
        return w('@font-face {font-family:"font";src:url("https://")}', function(c, f) {
            var b = e.getElementById("smodernizr"),
                b = (b =
                    b.sheet || b.styleSheet) ? b.cssRules && b.cssRules[0] ? b.cssRules[0].cssText : b.cssText || "" : "";
            a = /src/i.test(b) && 0 === b.indexOf(f.split(" ")[0])
        }), a
    };
    d.generatedcontent = function() {
        var a;
        return w('#modernizr{font:0/0 a}#modernizr:after{content:":)";visibility:hidden;font:3px/1 a}', function(c) {
            a = 3 <= c.offsetHeight
        }), a
    };
    d.video = function() {
        var a = e.createElement("video"),
            c = !1;
        try {
            if (c = !!a.canPlayType) c = new Boolean(c), c.ogg = a.canPlayType('video/ogg; codecs\x3d"theora"').replace(/^no$/, ""), c.h264 = a.canPlayType('video/mp4; codecs\x3d"avc1.42E01E"').replace(/^no$/,
                ""), c.webm = a.canPlayType('video/webm; codecs\x3d"vp8, vorbis"').replace(/^no$/, "")
        } catch (b) {}
        return c
    };
    d.audio = function() {
        var a = e.createElement("audio"),
            c = !1;
        try {
            if (c = !!a.canPlayType) c = new Boolean(c), c.ogg = a.canPlayType('audio/ogg; codecs\x3d"vorbis"').replace(/^no$/, ""), c.mp3 = a.canPlayType("audio/mpeg;").replace(/^no$/, ""), c.wav = a.canPlayType('audio/wav; codecs\x3d"1"').replace(/^no$/, ""), c.m4a = (a.canPlayType("audio/x-m4a;") || a.canPlayType("audio/aac;")).replace(/^no$/, "")
        } catch (b) {}
        return c
    };
    d.localstorage =
        function() {
            try {
                return localStorage.setItem("modernizr", "modernizr"), localStorage.removeItem("modernizr"), !0
            } catch (a) {
                return !1
            }
        };
    d.sessionstorage = function() {
        try {
            return sessionStorage.setItem("modernizr", "modernizr"), sessionStorage.removeItem("modernizr"), !0
        } catch (a) {
            return !1
        }
    };
    for (var x in d) F(d, x) && (t = x.toLowerCase(), g[t] = d[x](), v.push((g[t] ? "" : "no-") + t));
    g.addTest = function(a, c) {
        if ("object" == typeof a)
            for (var b in a) F(a, b) && g.addTest(b, a[b]);
        else {
            a = a.toLowerCase();
            if (g[a] !== B) return g;
            c = "function" ==
                typeof c ? c() : c;
            s.className += " " + (c ? "" : "no-") + a;
            g[a] = c
        }
        return g
    };
    z.cssText = "";
    var d = null,
        J = function() {
            var a = i.elements;
            return "string" == typeof a ? a.split(" ") : a
        },
        G = function(a) {
            var c = N[a[b]];
            return c || (c = {}, p++, a[b] = p, N[p] = c), c
        },
        r = function(a, c, b) {
            c || (c = e);
            if (h) return c.createElement(a);
            b || (b = G(c));
            var d;
            return b.cache[a] ? d = b.cache[a].cloneNode() : L.test(a) ? d = (b.cache[a] = b.createElem(a)).cloneNode() : d = b.createElem(a), d.canHaveChildren && !M.test(a) && !d.tagUrn ? b.frag.appendChild(d) : d
        };
    t = function(a) {
        a || (a =
            e);
        var c = G(a);
        if (i.shivCSS && !o && !c.hasCSS) {
            var b, d = a;
            b = d.createElement("p");
            d = d.getElementsByTagName("head")[0] || d.documentElement;
            b = (b.innerHTML = "x\x3cstyle\x3earticle,aside,dialog,figcaption,figure,footer,header,hgroup,main,nav,section{display:block}mark{background:#FF0;color:#000}template{display:none}\x3c/style\x3e", d.insertBefore(b.lastChild, d.firstChild));
            c.hasCSS = !!b
        }
        if (!h) {
            var k = a;
            c.cache || (c.cache = {}, c.createElem = k.createElement, c.createFrag = k.createDocumentFragment, c.frag = c.createFrag());
            k.createElement = function(a) {
                return i.shivMethods ? r(a, k, c) : c.createElem(a)
            };
            k.createDocumentFragment = Function("h,f", "return function(){var n\x3df.cloneNode(),c\x3dn.createElement;h.shivMethods\x26\x26(" + J().join().replace(/[\w\-]+/g, function(a) {
                return c.createElem(a), c.frag.createElement(a), 'c("' + a + '")'
            }) + ");return n}")(i, c.frag)
        }
        return a
    };
    x = this.html5 || {};
    var M = /^<|^(?:button|map|select|textarea|object|iframe|option|optgroup)$/i,
        L = /^(?:a|b|code|div|fieldset|h1|h2|h3|h4|h5|h6|i|label|li|ol|p|q|span|strong|style|table|tbody|td|th|tr|ul)$/i,
        o, b = "_html5shiv",
        p = 0,
        N = {},
        h;
    try {
        var j = e.createElement("a");
        j.innerHTML = "\x3cxyz\x3e\x3c/xyz\x3e";
        o = "hidden" in j;
        var n;
        if (!(n = 1 == j.childNodes.length)) {
            e.createElement("a");
            var k = e.createDocumentFragment();
            n = "undefined" == typeof k.cloneNode || "undefined" == typeof k.createDocumentFragment || "undefined" == typeof k.createElement
        }
        h = n
    } catch (y) {
        h = o = !0
    }
    var i = {
        elements: x.elements || "abbr article aside audio bdi canvas data datalist details dialog figcaption figure footer header hgroup main mark meter nav output progress section summary template time video",
        version: "3.7.0",
        shivCSS: !1 !== x.shivCSS,
        supportsUnknownElements: h,
        shivMethods: !1 !== x.shivMethods,
        type: "default",
        shivDocument: t,
        createElement: r,
        createDocumentFragment: function(a, c) {
            a || (a = e);
            if (h) return a.createDocumentFragment();
            c = c || G(a);
            for (var b = c.frag.cloneNode(), d = 0, k = J(), i = k.length; d < i; d++) b.createElement(k[d]);
            return b
        }
    };
    this.html5 = i;
    t(e);
    return g._version = "2.7.0", g._prefixes = D, g._domPrefixes = A, g._cssomPrefixes = u, g.hasEvent = H, g.testProp = function(a) {
            return C([a])
        }, g.testAllProps = m, g.testStyles =
        w, s.className = s.className.replace(/(^|\s)no-js(\s|$)/, "$1$2") + (" js " + v.join(" ")), g
}(this, this.document);
(function(l, e, B) {
    function C(b) {
        return "[object Function]" == E.call(b)
    }

    function m(b) {
        return "string" == typeof b
    }

    function g() {}

    function s(b) {
        return !b || "loaded" == b || "complete" == b || "uninitialized" == b
    }

    function d() {
        var b = t.shift();
        w = 1;
        b ? b.t ? A(function() {
            ("c" == b.t ? o.injectCss : o.injectJs)(b.s, 0, b.a, b.x, b.e, 1)
        }, 0) : (b(), d()) : w = 0
    }

    function z(b, g, l, h, j) {
        w = 0;
        g = g || "j";
        if (m(b)) {
            var n = "c" == g ? x : F,
                k = this.i++,
                y = function(c) {
                    if (!a && s(i.readyState) && (f.r = a = 1, !w && d(), i.onload = i.onreadystatechange = null, c)) {
                        "img" != n && A(function() {
                                I.removeChild(i)
                            },
                            50);
                        for (var k in r[b]) r[b].hasOwnProperty(k) && r[b][k].onload()
                    }
                };
            j = j || o.errorTimeout;
            var i = e.createElement(n),
                a = 0,
                c = 0,
                f = {
                    t: g,
                    s: b,
                    e: l,
                    a: h,
                    x: j
                };
            1 === r[b] && (c = 1, r[b] = []);
            "object" == n ? i.data = b : (i.src = b, i.type = n);
            i.width = i.height = "0";
            i.onerror = i.onload = i.onreadystatechange = function() {
                y.call(this, c)
            };
            t.splice(k, 0, f);
            "img" != n && (c || 2 === r[b] ? (I.insertBefore(i, K ? null : v), A(y, j)) : r[b].push(i))
        } else t.splice(this.i++, 0, b), 1 == t.length && d();
        return this
    }

    function D() {
        var b = o;
        return b.loader = {
            load: z,
            i: 0
        }, b
    }
    var u = e.documentElement,
        A = l.setTimeout,
        v = e.getElementsByTagName("script")[0],
        E = {}.toString,
        t = [],
        w = 0,
        H = "MozAppearance" in u.style,
        K = H && !!e.createRange().compareNode,
        I = K ? u : v.parentNode,
        u = l.opera && "[object Opera]" == E.call(l.opera),
        u = !!e.attachEvent && !u,
        F = H ? "object" : u ? "script" : "img",
        x = u ? "script" : F,
        J = Array.isArray || function(b) {
            return "[object Array]" == E.call(b)
        },
        G = [],
        r = {},
        M = {
            timeout: function(b, d) {
                return d.length && (b.timeout = d[0]), b
            }
        },
        L, o;
    o = function(b) {
        function d(b, e, i, a, c) {
            var f, g;
            g = b.split("!");
            var h = G.length,
                j = g.pop(),
                m = g.length,
                j = {
                    url: j,
                    origUrl: j,
                    prefixes: g
                },
                n, p, l;
            for (p = 0; p < m; p++) l = g[p].split("\x3d"), (n = M[l.shift()]) && (j = n(j, l));
            for (p = 0; p < h; p++) j = G[p](j);
            f = j;
            var o = f.autoCallback;
            f.url.split(".").pop().split("?").shift();
            f.bypass || (e && (e = C(e) ? e : e[b] || e[a] || e[b.split("/").pop().split("?")[0]]), f.instead ? f.instead(b, e, i, a, c) : (r[f.url] ? f.noexec = !0 : r[f.url] = 1, i.load(f.url, f.forceCSS || !f.forceJS && "css" == f.url.split(".").pop().split("?").shift() ? "c" : B, f.noexec, f.attrs, f.timeout), (C(e) || C(o)) && i.load(function() {
                D();
                e && e(f.origUrl,
                    c, a);
                o && o(f.origUrl, c, a);
                r[f.url] = 2
            })))
        }

        function e(b, h) {
            function i(b, c) {
                if (b)
                    if (m(b)) c || (f = function() {
                        var b = [].slice.call(arguments);
                        j.apply(this, b);
                        n()
                    }), d(b, f, h, 0, a);
                    else {
                        if (Object(b) === b)
                            for (o in l = function() {
                                    var a = 0,
                                        c;
                                    for (c in b) b.hasOwnProperty(c) && a++;
                                    return a
                                }(), b) b.hasOwnProperty(o) && (!c && !--l && (C(f) ? f = function() {
                                var a = [].slice.call(arguments);
                                j.apply(this, a);
                                n()
                            } : f[o] = function(a) {
                                return function() {
                                    var b = [].slice.call(arguments);
                                    a && a.apply(this, b);
                                    n()
                                }
                            }(j[o])), d(b[o], f, h, o, a))
                    }
                else !c && n()
            }
            var a = !!b.test,
                c = b.load || b.both,
                f = b.callback || g,
                j = f,
                n = b.complete || g,
                l, o;
            i(a ? b.yep : b.nope, !!c);
            c && i(c)
        }
        var h, j, n = this.yepnope.loader;
        if (m(b)) d(b, 0, n, 0);
        else if (J(b))
            for (h = 0; h < b.length; h++) j = b[h], m(j) ? d(j, 0, n, 0) : J(j) ? o(j) : Object(j) === j && e(j, n);
        else Object(b) === b && e(b, n)
    };
    o.addPrefix = function(b, d) {
        M[b] = d
    };
    o.addFilter = function(b) {
        G.push(b)
    };
    o.errorTimeout = 1E4;
    null == e.readyState && e.addEventListener && (e.readyState = "loading", e.addEventListener("DOMContentLoaded", L = function() {
        e.removeEventListener("DOMContentLoaded",
            L, 0);
        e.readyState = "complete"
    }, 0));
    l.yepnope = D();
    l.yepnope.executeStack = d;
    l.yepnope.injectJs = function(b, p, l, h, j, n) {
        var k = e.createElement("script"),
            m, i;
        h = h || o.errorTimeout;
        k.src = b;
        for (i in l) k.setAttribute(i, l[i]);
        p = n ? d : p || g;
        k.onreadystatechange = k.onload = function() {
            !m && s(k.readyState) && (m = 1, p(), k.onload = k.onreadystatechange = null)
        };
        A(function() {
            m || (m = 1, p(1))
        }, h);
        j ? k.onload() : v.parentNode.insertBefore(k, v)
    };
    l.yepnope.injectCss = function(b, l, m, h, j, n) {
        h = e.createElement("link");
        var k;
        l = n ? d : l || g;
        h.href = b;
        h.rel = "stylesheet";
        h.type = "text/css";
        for (k in m) h.setAttribute(k, m[k]);
        j || (v.parentNode.insertBefore(h, v), A(l, 0))
    }
})(this, document);
Modernizr.load = function() {
    yepnope.apply(window, [].slice.call(arguments, 0))
};

$(document).ready(function() {
    document.getElementById("contact-card");
    $(".contact").on('click', function() {
        $("#contact-content").is(":hidden") ? ($(".contact").addClass("open"), $(".topToolbarContent").addClass("open"), $("#contact-content").slideDown("slow")) : close()
    });
    $(".close-content").on('click', function() {
        close()
    })
});

function close() {
    $(".contact").removeClass("open");
    $(".topToolbarContent").removeClass("open");
    $("#contact-content").slideUp("slow")
}

function openChatWindow() {
    "undefined" === typeof chatWindow ? chatWindow = window.open("https://shaw.custhelp.com/app/chat/chat_launch", "chatWindow", "width\x3d820,height\x3d600,toolbars\x3dno,menubar\x3dno,location\x3dno,scrollbars\x3dno,status\x3dno") : null == chatWindow ? chatWindow = window.open("https://shaw.custhelp.com/app/chat/chat_launch", "chatWindow", "width\x3d820,height\x3d600,toolbars\x3dno,menubar\x3dno,location\x3dno,scrollbars\x3dno,status\x3dno") : null == chatWindow.closed ? chatWindow = window.open("https://shaw.custhelp.com/app/chat/chat_launch",
        "chatWindow", "width\x3d820,height\x3d600,toolbars\x3dno,menubar\x3dno,location\x3dno,scrollbars\x3dno,status\x3dno") : "undefined" == typeof chatWindow.closed ? chatWindow = window.open("https://shaw.custhelp.com/app/chat/chat_launch", "chatWindow", "width\x3d820,height\x3d600,toolbars\x3dno,menubar\x3dno,location\x3dno,scrollbars\x3dno,status\x3dno") : !1 === chatWindow.closed ? chatWindow.trigger("focus") : !0 === chatWindow.closed && (chatWindow = window.open("https://shaw.custhelp.com/app/chat/chat_launch", "chatWindow", "width\x3d820,height\x3d600,toolbars\x3dno,menubar\x3dno,location\x3dno,scrollbars\x3dno,status\x3dno"))
}

function openEmailWindow() {
    window.open("https://shaw.custhelp.com/app/ask", "emailWindow", "width\x3d820,height\x3d600,toolbars\x3dno,menubar\x3dno,location\x3dno,scrollbars\x3dno,status\x3dno")
}
var supportsTransitions = function() {
    var a = document.createElement("p").style,
        b = ["ms", "O", "Moz", "Webkit"];
    if ("" == a.transition) return !0;
    for (; b.length;)
        if (b.pop() + "Transition" in a) return !0;
    return !1
}();
(function(b, f) {
    function h(a, i) {
        this.$element = b(a);
        this.settings = b.extend({}, j, i);
        this.init()
    }
    var j = {
        slideInput: !0,
        labelStartTop: "26px",
        labelEndTop: "20px",
        transitionDuration: 0.3,
        transitionEasing: "ease-in-out",
        labelClass: "",
        typeMatches: /tel|text|password|email|number|search|url|hidden/
    };
    h.prototype = {
        init: function() {
            var a = this,
                b = {
                    "-webkit-transition": "all " + this.settings.transitionDuration + "s " + this.settings.transitionEasing,
                    "-moz-transition": "all " + this.settings.transitionDuration + "s " + this.settings.transitionEasing,
                    "-o-transition": "all " + this.settings.transitionDuration + "s " + this.settings.transitionEasing,
                    "-ms-transition": "all " + this.settings.transitionDuration + "s " + this.settings.transitionEasing,
                    transition: "all " + this.settings.transitionDuration + "s " + this.settings.transitionEasing
                };
            if ("INPUT" === this.$element.prop("tagName").toUpperCase() && this.settings.typeMatches.test(this.$element.attr("type"))) {
                var c = this.$element.attr("id");
                c || (c = Math.floor(100 * Math.random()) + 1, this.$element.attr("id", c));
                var d = this.$element.attr("placeholder"),
                    e = this.$element.data("label"),
                    g = this.$element.data("class");
                g || (g = "");
                if (!d || "" === d) d = "You forgot to add placeholder attribute!";
                if (!e || "" === e) e = d;
                this.inputPaddingTop = parseFloat(this.$element.css("padding-top")) + 12;
                this.$element.wrap('\x3cdiv class\x3d"floatlabel-wrapper" style\x3d"position:relative"\x3e\x3c/div\x3e');
                this.$element.before('\x3clabel for\x3d"' + c + '" class\x3d"label-floatlabel ' + this.settings.labelClass + " " + g + '"\x3e' + e + "\x3c/label\x3e");
                this.$label = this.$element.prev("label");
                this.$label.css({
                    position: "absolute",
                    top: this.settings.labelStartTop,
                    left: this.$element.css("padding-left"),
                    "font-style": "Arial",
                    color: "#666666",
                    "font-size": "12px",
                    "font-weight": "normal",
                    display: "none",
                    "-moz-opacity": "0",
                    "-khtml-opacity": "0",
                    "-webkit-opacity": "0",
                    opacity: "0"
                });
                this.settings.slideInput || this.$element.css({
                    "padding-top": this.inputPaddingTop
                });
                this.$element.on("keyup blur change", function(b) {
                    a.checkValue(b)
                });
                f.setTimeout(function() {
                    a.$label.css(b);
                    a.$element.css(b)
                }, 100);
                this.checkValue()
            }
        },
        checkValue: function(a) {
            a && 9 ===
                (a.keyCode || a.which) || (a = this.$element.data("flout"), "" !== this.$element.val() && this.$element.data("flout", "1"), "" === this.$element.val() && this.$element.data("flout", "0"), "1" === this.$element.data("flout") && "1" !== a && this.showLabel(), "0" === this.$element.data("flout") && "0" !== a && this.hideLabel())
        },
        showLabel: function() {
            var a = this;
            a.$label.css({
                display: "block"
            });
            f.setTimeout(function() {
                a.$label.css({
                    top: a.settings.labelEndTop,
                    "-moz-opacity": "1",
                    "-khtml-opacity": "1",
                    "-webkit-opacity": "1",
                    opacity: "1"
                });
                a.settings.slideInput &&
                    a.$element.css({
                        "padding-top": a.inputPaddingTop
                    })
            }, 50)
        },
        hideLabel: function() {
            var a = this;
            a.$label.css({
                top: a.settings.labelStartTop,
                "-moz-opacity": "0",
                "-khtml-opacity": "0",
                "-webkit-opacity": "0",
                opacity: "0"
            });
            a.settings.slideInput && a.$element.css({
                "padding-top": parseFloat(a.inputPaddingTop) - 12
            });
            f.setTimeout(function() {
                a.$label.css({
                    display: "none"
                })
            }, 1E3 * a.settings.transitionDuration)
        }
    };
    b.fn.floatlabel = function(a) {
        return this.each(function() {
            b.data(this, "plugin_floatlabel") || b.data(this, "plugin_floatlabel",
                new h(this, a))
        })
    }
})(jQuery, window, document);
(function(k, g, d) {
    function o(b) {
        var a = {},
            c = /^jQuery\d+$/;
        d.each(b.attributes, function(b, d) {
            d.specified && !c.test(d.name) && (a[d.name] = d.value)
        });
        return a
    }

    function h(b, a) {
        var c = d(this);
        if ((this.value == c.attr("placeholder") || "Email address" == this.value || "Username" == this.value || "Account number" == this.value) && c.hasClass("placeholder"))
            if (c.data("placeholder-password")) {
                c = c.hide().next().show().attr("id", c.removeAttr("id").data("placeholder-id"));
                if (!0 === b) return c[0].value = a;
                c.trigger("focus")
            } else this.value = "",
                c.removeClass("placeholder"), this == l() && this.select()
    }

    function j() {
        var b, a = d(this),
            c = this.id;
        if ("" == this.value || "Email address" == this.value || "Username" == this.value || "Account number" == this.value) {
            if ("password" == this.type) {
                if (!a.data("placeholder-textinput")) {
                    try {
                        b = a.clone().attr({
                            type: "text"
                        })
                    } catch (e) {
                        b = d("\x3cinput\x3e").attr(d.extend(o(this), {
                            type: "text"
                        }))
                    }
                    b.removeAttr("name").data({
                        "placeholder-password": a,
                        "placeholder-id": c
                    }).bind("focus.placeholder", h);
                    a.data({
                        "placeholder-textinput": b,
                        "placeholder-id": c
                    }).before(b)
                }
                a =
                    a.removeAttr("id").hide().prev().attr("id", c).show()
            }
            a.addClass("placeholder");
            a[0].value = a.attr("placeholder")
        } else a.removeClass("placeholder")
    }

    function l() {
        try {
            return g.activeElement
        } catch (b) {}
    }
    var f = "[object OperaMini]" == Object.prototype.toString.call(k.operamini),
        i = "placeholder" in g.createElement("input") && !f,
        f = "placeholder" in g.createElement("textarea") && !f,
        e = d.fn,
        m = d.valHooks,
        n = d.propHooks;
    i && f ? (e = e.placeholder = function() {
        return this
    }, e.input = e.textarea = !0) : (e = e.placeholder = function() {
        this.filter((i ?
            "textarea" : ":input") + "[placeholder]").not(".placeholder").bind({
            "focus.placeholder": h,
            "blur.placeholder": j
        }).data("placeholder-enabled", !0).trigger("blur.placeholder");
        return this
    }, e.input = i, e.textarea = f, e = {
        get: function(b) {
            var a = d(b),
                c = a.data("placeholder-password");
            return c ? c[0].value : a.data("placeholder-enabled") && a.hasClass("placeholder") ? "" : b.value
        },
        set: function(b, a) {
            var c = d(b),
                e = c.data("placeholder-password");
            if (e) return e[0].value = a;
            if (!c.data("placeholder-enabled")) return b.value = a;
            "" == a ? (b.value =
                a, b != l() && j.call(b)) : c.hasClass("placeholder") ? h.call(b, !0, a) || (b.value = a) : b.value = a;
            return c
        }
    }, i || (m.input = e, n.value = e), f || (m.textarea = e, n.value = e), d(function() {
        d(g).delegate("form", "submit.placeholder", function() {
            var b = d(".placeholder", this).each(h);
            setTimeout(function() {
                b.each(j)
            }, 10)
        })
    }), d(k).bind("beforeunload.placeholder", function() {
        d(".placeholder").each(function() {
            this.value = ""
        })
    }))
})(this, document, jQuery);
var analyticsSignon = {
        realm: "",
        redirectURL: "",
        signonClick: function() {
            var a = this;
            $("button.account_number_popover").on('click', function() {
                $("body").trigger({
                    type: "action",
                    event: "signon",
                    value: "signon|account-number-modal-open"
                })
            });
            $("button#signin_submit").on('click', function() {
                $("body").trigger({
                    type: "action",
                    event: "signon",
                    value: "signon|signon-start|" + a.realm
                })
            })
        },
        signonFormSubmitOnError: function(a) {
            "undefined" !== typeof utag && utag.link({
                site_section: "sign-on-and-register",
                sub_section: "sign-on-and-register|register",
                link_description: "sign-on-and-register|register|account-info-error|" + a,
                link_name: "form error",
                my_account_register_form_status: "error"
            })
        },
        signonFormSubmitOnSuccess: function(a, b) {
            "undefined" !== typeof utag && utag.link({
                site_section: "sign-on-and-register",
                sub_section: "sign-on-and-register|login",
                link_description: "sign-on-and-register|login|confirm|" + a,
                link_name: "form click",
                my_account_sign_on_form_status: "confirm",
                login_redirect_destination: b
            })
        }
    },
    analyticsRegisterForgot = {
        forgot: "",
        ip_validated: "",
        redirectURL: "",
        getPage: function() {
            return 1 == self.forgot ? "forgot" : "register"
        },
        registerForgotClicks: function() {
            var a = this;
            $("button#account_number_popover").on("click", function() {
                var b = a.getPage();
                $("body").trigger({
                    type: "action",
                    event: b,
                    value: b + "|step-1|account-number-modal-open"
                })
            });
            $("button#phone_number_popover").on("click", function() {
                var b = a.getPage();
                $("body").trigger({
                    type: "action",
                    event: b,
                    value: b + "|step-1|phone-number-modal-open"
                })
            });
            $("button#create_password_popover").on("click", function() {
                var b = a.getPage();
                $("body").trigger({
                    type: "action",
                    event: b,
                    value: b + "|step-2|password-modal-open"
                })
            });
            $(".cancel").on("click", function() {
                var b = a.getPage();
                $("body").trigger({
                    type: "action",
                    event: b,
                    value: b + "|step-2|clicked-cancel"
                })
            })
        },
        ipValidated: function() {
            if (this.ip_validated) {
                var a = this.getPage();
                $("body").trigger({
                    type: "action",
                    event: a,
                    value: a + "|step-1|start-shawmodem"
                })
            } else a = this.getPage(), $("body").trigger({
                type: "action",
                event: a,
                value: a + "|step-1|start-noshawmodem"
            })
        },
        accountNumberError: function() {
            var a = this.getPage();
            $("body").trigger({
                type: "action",
                event: a,
                value: a + "|step-1|account-number-error"
            })
        },
        phoneNumberInvalidError: function() {
            var a = this.getPage();
            $("body").trigger({
                type: "action",
                event: a,
                value: a + "|step-1|phone-number-error"
            })
        },
        phoneNumberNotOnAccountError: function() {
            var a = this.getPage();
            $("body").trigger({
                type: "action",
                event: a,
                value: a + "|step-1|phonenumber-not-on-account-error"
            })
        },
        postalCodeInvalidError: function() {
            var a = this.getPage();
            $("body").trigger({
                type: "action",
                event: a,
                value: a + "|step-1|invalid-postalcode-error"
            })
        },
        postalCodeNotOnAccountError: function() {
            var a =
                this.getPage();
            $("body").trigger({
                type: "action",
                event: a,
                value: a + "|step-1|postalcode-not-on-account-error"
            })
        },
        pageLoadOnSecondStep: function() {
            var a = this.getPage();
            $("body").trigger({
                type: "action",
                event: a,
                value: a + "|step-2|start"
            })
        },
        registerForgotSuccess: function() {
            "1" == this.forgot ? "undefined" !== typeof utag && utag.view({
                site_section: "sign-on-and-register",
                sub_section: "sign-on-and-register|forgot-password",
                page_name: "sign-on-and-register|forgot-password|reset-confirm",
                my_account_forgot_password_form_status: "confirm",
                login_redirect_destination: self.redirectURL
            }) : "undefined" !== typeof utag && utag.view({
                site_section: "sign-on-and-register",
                sub_section: "sign-on-and-register|register",
                page_name: "sign-on-and-register|register|confirm",
                my_account_register_form_status: "confirm",
                login_redirect_destination: self.redirectURL
            })
        }
    };
var shaw = "undefined" == typeof shaw ? {} : shaw;
shaw.signon = "undefined" == typeof shaw.signon ? {} : shaw.signon;
shaw.signon.createCookie = function(b, c, d) {
    var a = "";
    d && (a = new Date, a.setTime(a.getTime() + 864E5 * d), a = "; expires\x3d" + a.toGMTString());
    document.cookie = b + "\x3d" + c + a + "; path\x3d/"
};
shaw.signon.createCookieDomain = function(b, c, d, a) {
    var e = "";
    a && (e = new Date, e.setTime(e.getTime() + 864E5 * a), e = "; expires\x3d" + e.toGMTString());
    document.cookie = b + "\x3d" + c + e + "; path\x3d/;domain\x3d" + d
};
shaw.signon.readCookie = function(b) {
    for (var c = document.cookie.split(";"), d = 0; d < c.length; d++) {
        var a = c[d];
        if (-1 != a.indexOf(b)) return a = a.replace(/\s/g, ""), a.substring(b.length + 1, a.length)
    }
    return null
};
shaw.signon.deleteCookie = function(b) {
    shaw.signon.createCookie(b, "", -1)
};
shaw.signon.populateUsername = function() {
    var b = !1;
    $(".persistent_check").each(function() {
        var c = this.id.replace("persistent_check_", ""),
            d = shaw.signon.readCookie("loginUserCookie_" + c);
        null != d ? ($("#username_input_" + c).val(d).trigger("change"), $(this).prop("checked", !0), !1 == b && (b = !0, $("#password_input").trigger( "focus" ))) : ($("#signon_form_" + c).find(".username_input").val("").change(), $(this).prop("checked", !1), !1 == b && (b = !0, $("#username_input_" + c).trigger( "focus" )))
    })
};
shaw.signon.checkCookieSupport = function() {
    return !0 != navigator.cookieEnabled ? (alert("Sorry, cookies are not supported on this browser.\nYour user name will not be remembered."), !1) : !0
};

function init(a, b) {
    showTabs(a, b);
    checkFailedLogin(b);
    submitButton.init();
    analyticsSignon.signonClick();
    var c = $("#goto").val();
    setAnchorFromURL();
    analyticsSignon.redirectURL = c
}

function showTabs(a, b) {
    a = a.replace("[", "");
    a = a.replace("]", "");
    a = a.replace(/\s+/g, "");
    var c = a.split(",");
    showTabsForRealms(c, b);
    $("#shawEmailTab").on('click', function() {
        email()
    });
    $("#shawOCCTab").on('click', function() {
        occ()
    });
    $("#shawDirectTab").on('click', function() {
        shawDirect()
    })
}

function checkFailedLogin(a) {
    0 != $("#error_message").html().length && ($(".error").css("display", "inline-block"), $(window).load(function() {
        analyticsSignon.signonFormSubmitOnError(a)
    }))
}

function showTabsForRealms(a, b) {
    1 < a.length ? ($(".tabs-menu").show(), $("#tabs li").css("width", 100 / a.length + "%")) : $(".tabs-menu").hide();
    !1 === matchRealmsInRealmsArray(a, "email") && $("#shawEmailTab").remove();
    !1 === matchRealmsInRealmsArray(a, "occ") && $("#shawOCCTab").remove();
    !1 === matchRealmsInRealmsArray(a, "shawdirect") && $("#shawDirectTab").remove();
    showRealm(b)
}

function matchRealmsInRealmsArray(a, b) {
    for (var c = a.length; c--;)
        if (a[c] === b) return !0;
    return !1
}

function showRealm(a) {
    "email" == a ? (email(), showEmailTabActive()) : "occ" == a ? (occ(), showOCCTabActive()) : "shawdirect" == a && (shawDirect(), showShawdirectTabActive())
}

function manageCookie() {
    shaw.signon.populateUsername()
}
var submitButton = {
    init: function() {
        var a = this;
        $("form").on("keyup change paste", "input", function(e) {
            if (e.which && e.which == 13) {
                return;
            }
            a.checkForm()
        });
        setTimeout(function() {
            a.checkForm()
        }, 1E3);
        $("button.button").on('click', function() {
            var a = $(".persistent_check"),
                c = a.attr("id").replace("persistent_check_", "");
            a.is(":checked") && shaw.signon.checkCookieSupport() ? shaw.signon.createCookie("loginUserCookie_" + c, $("#username_input_" + c).val(), 30) : shaw.signon.deleteCookie("loginUserCookie_" + c)
        })
    },
    checkForm: function() {
        $("form").find("input[type\x3dtext],input[type\x3dpassword]").filter(function() {
            return "" ===
                $(this).val()
        }).length ? this.disable() : this.enable()
    },
    enable: function() {
        $("button.button").prop("disabled", false);
        $("button.button").removeClass("button_disabled");
        $("button.button").addClass("button_enabled")
    },
    disable: function() {
        $("button.button").attr("disabled", "disabled");
        $("button.button").removeClass("button_enabled");
        $("button.button").addClass("button_disabled")
    }
};

function manageUserNameInput(a) {
    var b = $(".username_input");
    b.prop("id", a);
    "shawdirect" == $("#realm_input").val() ? b.attr("maxlength", "13") : b.removeAttr("maxlength");
    manageCookie()
}

function email() {
    $("form").attr("name", "signon_form_email");
    $("form").attr("id", "signon_form_email");
    $("#singon_submit").attr("onclick", "return signon_form_validate_shaw_email();");
    $("#forgot_username_url").hide();
    $("#orWord").hide();
    $("#forgot_password_url").text("password");
    $("#forgot_password_url").attr("href", "https://signon.shaw.ca/?application\x3dmanage\x26goto\x3dhttps://my.shaw.ca/Internet/Manage");
    $(".side-create-account a").text("Create one now \x3e");
    $("#realm_input").val("email");
    $(".persistent_check").attr("id",
        "persistent_check_email");
    $("#checkboxMask").attr("for", "persistent_check_email");
    $("div.checkbox-section .checkbox-label \x3e label").text("Remember email address");
    $(".side-create-account a").attr("href", "https://signon.shaw.ca/?application\x3dmanage");
    $("#create_one_now").attr("href", "https://signon.shaw.ca/?application\x3dmanage");
    $(".modal-title").html("What's my Shaw email address?");
    $(".modal-para").html('If you are a Shaw Internet customer and don\'t have an @shaw.ca email address, please visit \x3ca href\x3d"https://my.shaw.ca"\x3eMy Shaw\x3c/a\x3e to create one.');
    $("#account_number_popover_username").show();
    $("#account_number_popover_password").hide();
    $("#username_input_label").text("Shaw Email");
    manageUserNameInput("username_input_email");
    submitButton.checkForm();
    analyticsSignon.realm = $("#realm_input").val()
}

function occ() {
    $("form").attr("name", "signon_form_occ");
    $("form").attr("id", "signon_form_occ");
    $("#singon_submit").attr("onclick", "return signon_form_validate_occ();");
    $("#forgot_username_url").show();
    $("#orWord").show();
    $("#forgot_username_url").text("username");
    $("#forgot_password_url").text("password");
    $("#forgot_username_url").attr("href", "https://register.shaw.ca/?forgot\x3d1");
    $("#forgot_password_url").attr("href", "https://register.shaw.ca/?forgot\x3d1");
    $(".side-create-account a").text("Create one now \x3e");
    $("#realm_input").val("occ");
    $(".persistent_check").attr("id", "persistent_check_occ");
    $("#checkboxMask").attr("for", "persistent_check_occ");
    $("div.checkbox-section .checkbox-label \x3e label").text("Remember Shaw email");
    $(".side-create-account a").attr("href", "https://register.shaw.ca/");
    $("#create_one_now").attr("href", "https://register.shaw.ca/");
    $(".modal-title").html("What's my Shaw email?");
    $(".modal-para").html('If you are a Shaw Internet customer and don\'t have an @shaw.ca email address, please visit \x3ca href\x3d"https://my.shaw.ca"\x3eMy Shaw\x3c/a\x3e to create one.');
    $("#account_number_popover_username").show();
    $("#account_number_popover_password").hide();
    $("#username_input_label").text("Shaw email");
    manageUserNameInput("username_input_occ");
    submitButton.checkForm();
    analyticsSignon.realm = $("#realm_input").val()
}

function shawDirect() {
    $("form").attr("name", "signon_form_shawdirect");
    $("form").attr("id", "signon_form_shawdirect");
    $("#singon_submit").attr("onclick", "return signon_form_validate_shawdirect();");
    $("#forgot_username_url").hide();
    $("#orWord").hide();
    $("#forgot_password_url").text("password");
    $("#forgot_password_url").attr("href", "https://secure.shawdirect.ca/english/customercare/selfserve/ForgotPassword.asp");
    $(".side-create-account a").text("Create one now \x3e");
    $("#realm_input").val("shawdirect");
    $(".persistent_check").attr("id", "persistent_check_shawdirect");
    $("#checkboxMask").attr("for", "persistent_check_shawdirect");
    $("div.checkbox-section .checkbox-label \x3e label").text("Remember account number");
    $(".side-create-account a").attr("href", "https://secure.shawdirect.ca/english/customercare/selfserve/register.asp");
    $("#create_one_now").attr("href", "https://secure.shawdirect.ca/english/customercare/selfserve/register.asp");
    $(".modal-title").html("What's my Shaw Direct password?");
    $(".modal-para").html('If you don\'t have a password for your Shaw Direct account, please \x3ca href\x3d"https://secure.shawdirect.ca/english/customercare/selfserve/register.asp"\x3eregister\x3c/a\x3e to create one.');
    $("#account_number_popover_username").hide();
    $("#account_number_popover_password").show();
    $("#username_input_label").text("Account number");
    manageUserNameInput("username_input_shawdirect");
    submitButton.checkForm();
    analyticsSignon.realm = $("#realm_input").val()
}

function showEmailTabActive() {
    $("#tabs #shawEmailTab").addClass("active");
    $("#tabs #shawOCCTab").removeClass("active");
    $("#tabs #shawDirectTab").removeClass("active")
}

function showOCCTabActive() {
    $("#tabs #shawEmailTab").removeClass("active");
    $("#tabs #shawOCCTab").addClass("active");
    $("#tabs #shawDirectTab").removeClass("active")
}

function showShawdirectTabActive() {
    $("#tabs #shawEmailTab").removeClass("active");
    $("#tabs #shawOCCTab").removeClass("active");
    $("#tabs #shawDirectTab").addClass("active")
}

function setAnchorFromURL() {
    var a = location.hash,
        b = a.indexOf("\x26"); - 1 < b && (a = a.substring(0, b));
    $("#anchor").val(a)
};
<script>
    import { Card, CardTitle} from "svelte-materialify";
</script>

<div class="about">
    <Card outlined style="background: #e3e3e3">
        <CardTitle style="font-weight: 600; white-space:nowrap">Hi-Rise: Beautiful Manhattan plots</CardTitle>
        <div class="content">
            blah blah blah etc.
        </div>
    </Card>
</div>

<style lang="scss">
    .about {
        gap: 1rem;
        display: flex;
        flex-direction: column;
        .content {
            padding: 1rem;
            padding-top: 0;
        }
    }
</style>